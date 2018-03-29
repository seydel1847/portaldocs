<a name="portal-forms"></a>
# Portal Forms


<a name="portal-forms-overview"></a>
## Overview

The Portal SDK includes extensive support for displaying and managing user input through the use of Forms. Forms offer the ability to take advantage of features like consistent form layout styles, form-integrated UI widgets, user input validation, and data change tracking.

Forms are created using `HTML` templates, `ViewModels`, and `EditScopes`. 

**NOTE**:  EditScopes are becoming obsolete.   It is recommended that extensions be developed without edit scopes, as specified in [portalfx-editscopeless-procedure.md](portalfx-editscopeless-procedure.md).

Developers can use standard `HTML` and **Knockout** to build forms, in addition to the following items for which  the SDK Framework includes support.

  * Labels
  
  * Validation, as in the following image

    ![alt-text](../media/portalfx-forms/forms.png "Forms Example") 

  * Change tracking

  * Form reset

  * Persisting edits across journeys and browser sessions

  Form controls are a subset of controls that allow users to input information.  These controls provide a consistent api surface for managing validation, dirty states, and user input.  They also provide a consistent layout structure.

<a name="portal-forms-overview-form-control-view-model-contract-properties"></a>
### Form control view model contract properties

**value**: The value property is bound to the value shown in the control – You can subscribe to it in order to respond to user input, and you can set it to update the widgets value programmatically.

**dirty**: The dirty property is bound to the edit state of the control.  It will change from false to true if the user changes the value property by interacting with the control.  Setting the value property programmatically will not affect the dirty state of the control.  Note: The framework will never reset this property from true back to false as the framework does not track the original values of the control.  To set (or reset) this property programmatically, just write to it as you would any other observable.

<a name="portal-forms-overview-form-layout"></a>
### Form Layout

Use form sections to group controls, and other sections, into structured layouts based on rows and columns. Form sections provide the following benefits.

* Predefined forms styles
* Maintains consistency with proven user usability tests
* Retains the flexibility to layout the forms in accordance with team designs.

Some form layout styles are as follows.

* Columns

![alt-text](../media/portalfx-ux-forms/columns.png "Columns")

* Create

![alt-text](../media/portalfx-ux-forms/create.png "Create")

* In-line labels

![alt-text](../media/portalfx-ux-forms/in_line.png "In-line")

* Full width

![alt-text](../media/portalfx-ux-forms/form_style_full_border.png "Full width")

<!--TODO:  Determine what is recommended instead of the custom layouts. -->

**NOTE**: Custom layouts are not recommended.
 
<a name="portal-forms-overview-form-content"></a>
### Form Content

Form-integrated controls are the UI widgets that are compatible with forms. They can be used in a majority of forms scenarios. They automatically enable good form patterns, built-in validation, and auto-tracking of changes. The controls playground is located at  [https://aka.ms/portalfx/playground](https://aka.ms/portalfx/playground), and it  allows them to build their own code instead of using the provided samples.

<a name="portal-forms-overview-form-topics"></a>
### Form Topics

There are a number of subtopics in the forms topic.  Sample source code is included in subtopics that discuss the various Azure SDK API items.

| API Topic                        | Document                                                                                     | 
| -------------------------------- | -------------------------------------------------------------------------------------------- | 
| Designing and Arranging the Form | [portalfx-forms-designing.md](portalfx-forms-designing.md)                                   |  
| Forms Construction               | [portalfx-forms-construction.md](portalfx-forms-construction.md)                             |  
| Integrating Forms with Commands  | [portalfx-forms-integrating-with-commands.md](portalfx-forms-integrating-with-commands.md)   | 
| Form Field Validation            | [portalfx-forms-field-validation.md](portalfx-forms-field-validation.md)                     | 
| Sample Extensions with Forms     | [portalfx-extensions-samples-forms.md](portalfx-extensions-samples-forms.md)                 |

For more information about how forms and parameters interact with an extension, see [portalfx-parameter-collection-overview.md](portalfx-parameter-collection-overview.md).

For more information about forms with editScopes, see  [portalfx-legacy-editscopes.md](portalfx-legacy-editscopes.md).

For more information about forms without editScopes, see  [portalfx-editscopeless-overview.md](portalfx-editscopeless-overview.md).

<a name="portal-forms-frequently-asked-questions"></a>
## Frequently asked questions

<a name="portal-forms-frequently-asked-questions-should-i-use-an-action-bar-or-a-commands-toolbar-on-my-form"></a>
### Should I use an action bar or a commands toolbar on my form?

It depends on the scenario that drives the UX. If the form will capture some data from the user and expect the blade to be closed after submitting the changes, then use an action bar, as specified in [portalfx-ux-create-forms.md#action-bar-+-blue-buttons](portalfx-ux-create-forms.md#action-bar-+-blue-buttons).  However, if the form will edit or update some data, and expect the user to make multiple changes before the blade is closed, then use commands, as specified in [portalfx-commands.md](portalfx-commands.md). 

* Action Bar

  The action bar will have one button whose label is something like "OK", "Create", or "Submit". The blade should automatically close immediately after the action bar button is clicked. Users can abandon the form by clicking the Close button that is located at the top right of the application bar. Developers can use a `ParameterProvider` to simplify the code, because it provisions the `editScope` and implicitly closes the blade based on clicking on the action bar. 

  Alternatively, the action bar can contain two buttons, like "OK" and "Cancel", but that requires further configuration. The two-button method is not recommended because the "Cancel" button is made redundant by the Close button.

* Commands
  
  Typically, the two commands at the top of the blade are the "Save" command and the "Discard" command. The user can make edits and click "Save" to commit the changes. The blade should show the appropriate UX for saving the data, and will stay on the screen after the data has been saved. The user can make further changes and click "Save" again. The user can also discard their changes by clicking "Discard". Once the user is satisfied with the changes, they can close the blade manually.
  
* * * 

<a name="portal-forms-glossary"></a>
## Glossary

 This section contains a glossary of terms and acronyms that are used in this document. For common computing terms, see [https://techterms.com/](https://techterms.com/). For common acronyms, see [https://www.acronymfinder.com](https://www.acronymfinder.com).

| Term                 | Meaning |
| ---                  | --- |
| compile-time verified lambda | A lambda expression that is verified at compile time.  |
| eirty | The contents of a textbox or similar object have been changed from the time that they were originally displayed or instantiated. Related to the most recent value of a variable or observable. |
| DOM              | Document Object Model   |
| journey  | A user-defined collection of Azure blades to which the user has navigated in order to accomplish a specific goal or task. A set of experiences, each of which has its own goals, that combine to result in a greater level of competency or knowledge. |
| lambda expression | An anonymous function that is used to create delegates or expression tree types. |
| observable | Special Knockout or JavaScript objects that can notify subscribers or other code about changes, and can automatically detect dependencies.  |
| observable array | An observable that allows code to to detect and respond to changes on  a collection of things.   |
| promise | An object that is returned from asynchronous processing which binds together the results of multiple asynchronous operations.  This is in accordance with a contract that async operation(s) will either complete successfully or will have been rejected. | 
| property bag | A container that contains different types of object properties. Allows the   addition of properties without modifying the server side object, and with minimal changes to the client code.|
| validation |  The process of ensuring that form or field contents are within the specified constraints for an application.  This includes items like field length or numeric checks. |