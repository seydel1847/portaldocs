
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

### Form control view model contract properties

**value**: The value property is bound to the value shown in the control – You can subscribe to it in order to respond to user input, and you can set it to update the widgets value programmatically.

**dirty**: The dirty property is bound to the edit state of the control.  It will change from false to true if the user changes the value property by interacting with the control.  Setting the value property programmatically will not affect the dirty state of the control.  Note: The framework will never reset this property from true back to false as the framework does not track the original values of the control.  To set (or reset) this property programmatically, just write to it as you would any other observable.

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
 
### Form Content

Form-integrated controls are the UI widgets that are compatible with forms. They can be used in a majority of forms scenarios. They automatically enable good form patterns, built-in validation, and auto-tracking of changes. The controls playground is located at  [https://aka.ms/portalfx/playground](https://aka.ms/portalfx/playground), and it  allows them to build their own code instead of using the provided samples.

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