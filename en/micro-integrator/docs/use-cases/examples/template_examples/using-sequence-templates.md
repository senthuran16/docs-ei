# Using Sequence Templates

See the examples given below.

!!! Info
    The **Call Template** mediator allows you to construct a sequence by passing values into a **sequence template**. This is currently only supported for special types of mediators such as the **Iterator** and **Aggregate Mediators**, where actual XPath operations are performed on a different SOAP message, and not on the message coming into the mediator.

Sequence template parameters can be referenced using an XPath expression defined inside the in-line sequence. For example, the parameter named "foo" can be referenced by the Property mediator (defined inside the in-line sequence of the template) in the following ways:

`<property name=”fooValue” expression=”$func:foo” />`

or

`<property name=”fooValue” expression=”get-property('foo','func')” />`

Using function scope or "?func?" in the XPath expression allows us to refer to a particular parameter value passed externally by an invoker
such as the Call Template mediator.

## Example 1
Let's illustrate the sequence template with a simple example. Suppose we have a sequence that logs the text "hello" in three different languages. We shall make use of a proxy to which we shall send a payload. The switch statement will log a greeting based on the language

```xml
<proxy name="HelloProxy" startOnLoad="true" transports="http https" xmlns="http://ws.apache.org/ns/synapse">
    <target>
        <inSequence>
            <switch source="//lang[1]/text()">
                <case regex="English">
                  <log level="custom">
                    <property name="GREETING_MESSAGE" value="Hello"/>
                  </log>
                </case>
                <case regex="French">
                  <log level="custom">
                    <property name="GREETING_MESSAGE" value="Bonjour"/>
                  </log>
                </case>
                <case regex="Japanese">
                  <log level="custom">
                    <property name="GREETING_MESSAGE" value="Konnichiwa"/>
                  </log>
                </case>
                <default>
                  <log level="custom">
                    <property name="GREETING_MESSAGE" value="??"/>
                  </log>
                </default>
            </switch>
            <drop/>
        </inSequence>
        <outSequence/>
        <faultSequence/>
    </target>
</proxy>
```

Instead of printing our "hello" message for each and every language inside the sequence, we can create a generalized template of these actions, which will accept any greeting message (from a particular language) and log it on screen. For example, let's create the following template named "Hello_Logger". Thus, due to the availability of the Call Template mediator, you are not required to have the message entered in all four languages included in the sequence template configuration itself.


```xml
<template name="Hello_Logger" xmlns="http://ws.apache.org/ns/synapse">
    <parameter name="message"/>
    <sequence>
        <log level="custom">
            <property expression="$func:message" name="GREETING_MESSAGE"/>
        </log>
    </sequence>
</template>
```

The following four Call Template mediator configurations populate a sequence template named Hello_Logger with the "Hello" text in four different languages.

``` 
<call-template target="Hello_Logger">
  <with-param name="message" value="Hello" />
</call-template>
```

```
<call-template target="Hello_Logger">
   <with-param name="message" value="Bonjour" />
</call-template>
```

```
<call-template target="Hello_Logger">
  <with-param name="message" value="Konnichiwa" />
</call-template>
```

```
<call-template target="Hello_Logger">
  <with-param name="message" value="??" />
</call-template>
```

With our "Hello_Logger" in place, the Call Template mediator can
populate this template with actual hello messages and execute the
sequence of actions defined within the template like with any other
sequence. This is illustrated below.

```xml
<proxy name="HelloProxy" startOnLoad="true" transports="http https" xmlns="http://ws.apache.org/ns/synapse">
    <target>
        <inSequence>
            <switch source="//lang[1]/text()">
                <case regex="English">
                    <call-template target="Hello_Logger">
                        <with-param name="message" value="Hello"/>
                    </call-template>
                </case>
                <case regex="French">
                    <call-template target="Hello_Logger">
                        <with-param name="message" value="Bonjour"/>
                    </call-template>
                </case>
                <case regex="Japanese">
                    <call-template target="Hello_Logger">
                        <with-param name="message" value="Konnichiwa"/>
                    </call-template>
                </case>
                <default>
                    <call-template target="Hello_Logger"/>
                </default>
            </switch>
            <drop/>
        </inSequence>
        <outSequence/>
        <faultSequence/>
    </target>
</proxy>
```

The Call Template mediator points to the same template "Hello_Logger" and passes different arguments to it. In this way, sequence templates make it easy to stereotype different workflows inside the Micro Integrator.

You can test this out with the following payload sent to the proxy via `localhost:9290/services/HelloProxy`

```xml
<body>
    <lang>English</lang>
    <lang>French</lang>
    <lang>Japanese</lang>
</body>
```

!!! Note
    The `target` attribute is used to specify the sequence template you want to use. The `<with-param>` element is used to parse parameter values to the target sequence template. The parameter names should be the same as the names specified in target template. The parameter value can contain a string, an XPath expression (passed in with curly braces { }), or a dynamic XPath expression (passed in with double curly braces) of which the values are compiled dynamically.

## Example 2

The following Call Template mediator configuration populates a sequence template named `Testtemp` with a dynamic XPath expression.

```
<call-template target="Testtemp">
  <with-param name="message_store" value="<MESSAGE_STORE_NAME>" />
</call-template>
```

The following `Testtemp` template includes a dynamic XPath expression to save messages in a Message Store, which is dynamically set via the message context.

```
<template name="Testtemp" xmlns="http://ws.apache.org/ns/synapse">
    <parameter name="message_store"/>
    <sequence>
        <log level="custom">
          <property expression="$func:message_store"
                        name="STORENAME"
                        xmlns:ns="http://org.apache.synapse/xsd"
                        xmlns:ns2="http://org.apache.synapse/xsd" xmlns:soapenv="http://www.w3.org/2003/05/soap-envelope"/>
        </log>
        <store messageStore="{$func:message_store}"
                    xmlns:ns="http://org.apache.synapse/xsd"
                    xmlns:ns2="http://org.apache.synapse/xsd" xmlns:soapenv="http://www.w3.org/2003/05/soap-envelope"/>
    </sequence>
</template>
```