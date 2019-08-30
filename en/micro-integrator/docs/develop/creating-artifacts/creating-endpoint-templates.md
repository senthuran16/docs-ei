# Creating Endpoint Templates

Follow the instructions given below to create a new Endpoint Template in WSO2 Integration Studio.

## Instructions

Follow these steps to create a new scheduled task.

1.  Right click the project and go to **New → Template** to open the **New Template Artifact** dialog.
2.  Type a unique name for the template and specify the type of template you are creating.
    <table>
        <tr>
            <th>Template Type</th>
            <th>Description</th>
        </tr>
        <tr>
            <td><b>Address Endpoint Template</b></td>
            <td>
                The following information needs to be specified:
                <ul>
                    <li><b>Template Name</b>: The unique name for the endpoint template.</li>
                    <li><b>Name</b>: A name for the inline endpoint.</li>
                    <li><b>Address</b>: The URL of the template endpoint. This can be a parametrized value such as `          $uri         ` .</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><b>Default Endpoint Template</b></td>
            <td>
                The following information needs to be specified:
                <ul>
                    <li><b>Template Name</b>: The unique name for the endpoint template.</li>
                    <li><b>Name</b>: A name for the inline endpoint.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><b>WSDL Endpoint Template</b></td>
            <td>
                The following information needs to be specified:
                <ul>
                    <li><b>Template Name</b>: The unique name for the template.</li>
                    <li><b>Name</b>: A name for the inline endpoint.</li>
                    <li><b>Specify As</b>: The method to specify the WSDL. The available values are as follows:
                        <ul>
                            <li><b>In-lined WSDL</b>: Paste the WSDL in the text box that appears when this option is selected.
                            </li>
                            <li><b>URI</b>: Activates the WSDL URI field.</li>
                        </ul>
                    </li>
                    <li><b>WSDL URI</b>: The URI of the WSDL.</li>
                    <li><b>Service</b>: The service selected from the available services for the WSDL.</li>
                    <li><b>Port</b>: The port selected for the service specified in the above
                        field. In a WSDL an endpoint is bound to each port inside each service.
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td><b>HTTP Endpoint Template</b></td>
            <td>
                You can define a URI template based REST service endpoint. The Endpoint Template has the following options:
                <ul>
                    <li><b>Template Name</b>: The unique name for the endpoint template.</li>
                    <li><b>Name</b>: A name for the inline endpoint.</li>
                    <li><b>URI Template</b>: The URI template of the endpoint. Insert `          uri.var.         ` before each variable. Click **Test** to test the URI.</li>
                </ul>
            </td>
        </tr>
    </table>

3.  Do one of the following:  
    -   To save the endpoint in an existing ESB Config project in your workspace, click **Browse** and select that project.
    -   To save the endpoint in a new ESB Config project, click **Create new Project** and create the new project.
4.  Click **Finish** . The template is created in the `src/main/synapse-config/templates` folder under the ESB Config project you specified.
5.  Open the new artifact from the project explorer, and update any [optional endpoint template properties](../../creating-projects/#esb-config-project).

## Examples
..

## Guides