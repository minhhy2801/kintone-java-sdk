---
id: app
title: App
sidebar_label: App
---

Gets general information of an App, including the name, description, related Space, creator and updater information.

> - Permissions to view the App is needed.
> - API Tokens cannot be used with this API.

## Constructor

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| connection | [Connection](../connection) | yes | The connection module of this SDK.

**Sample code**

<details class="tab-container" open>
<Summary>Init app module</Summary>

**Source code**

```java  
// Init authentication
Auth kintoneAuth = new Auth()

// Password Authentication
String username = "your_usernamr"
String password = "your_password"
kintoneAuth = kintoneAuth.setPasswordAuth(username, password)
Connection connection = Connection( "your_domain", kintoneAuth )
App app = new App(connection)

```

</details>

## Methods

### getApp(Integer appId)

> Get single app

#**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| appId | Integer | yes | The kintone app ID

**Return**

[AppModel](../model/app/app/app-model)

**Sample code**

<details class="tab-container" open>
<Summary>get App</Summary>

**Source code**
```java  
Integer appId = {your_app_id};
App appManagerment = new App(connection);
AppModel app = appManagerment.getApp(appId);

```

</details>

### getApps(Integer offset, Integer limit)

> Get multiple apps

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| offset | Integer | (optional) | The offset off data result
| limit | Integer | (optional) | The limit number of result

**Return**

List<[AppModel](../model/app/app/app-model)>

**Sample code**

<details class="tab-container" open>
<Summary>Get Apps</Summary>

**Source code**

```java  
Integer offset = 10;
Integer limit = 50;

App appManagerment = new App(connection);
List<AppModel> appList = appManagerment.getApps(offset, limit);
```

</details>

### getAppsByIDs(List<Integer> ids, Integer offset, Integer limit)

> Get multiple apps by list of ids

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| ids | List<Integer\> | yes | The array of app ids
| offset | Integer | (optional) | The offset off data result
| limit | Integer | (optional) | The limit number of result

**Return**

List<[AppModel](../model/app/app/app-model)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By IDs</Summary>

**Source code**

```java  
List<Integer> appIds = new List<Integer>();
appIds.add({your_app_id});
appIds.add({your_app_id});
Integer offset = {your_limit};
Integer limit = {your_offset};

App appManagerment = new App(connection);
List<AppModel> appList = appManagerment.getAppsByIDs(appIds, offset, limit);
```

</details>

### getAppsByCodes(List<String> codes, Integer offset, Integer limit)

> Get multiple apps by a list of codes

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| codes | List<String\> | yes | The array of app codes
| offset | Integer | (optional) | The offset off data result
| limit | Integer | (optional) | The limit number of result

**Return**

List<[AppModel](../model/app/app/app-model)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By Codes</Summary>

**Source code**

```java  
List<String> appCode = new List<String>();
appCode.add({your_app_code});
appCode.add({your_app_code});
Integer limit = {your_limit};
Integer offset = {your_offset};

App appManagerment = new App(connection);
List<AppModel> appList = appManagerment.getAppsByCodes(appCode, offset, limit);
```

</details>

### getAppsByName(String name, Integer offset, Integer limit)

> Get multiple apps by name

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| name | String | yes | The app name
| offset | Integer | (optional) | The offset off data result
| limit | Integer | (optional) | The limit number of result

**Return**

List<[AppModel](../model/app/app/app-model)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By Name</Summary>

**Source code**

```java  
String appName = {your_app_name};
Integer offset = {your_offset};
Integer limit = {your_limit};

App appManagerment = new App(connection);
List<AppModel> appLlist = appManagerment.getAppsByName(name, offset, limit);
```

</details>

### getAppsBySpaceIDs(List<Integer> spaceIds, Integer offset, Integer limit)

> Get multiple apps by list of space's ids

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| spaceIds | List<Integer\> | yes | The array of space ids
| offset | Integer | (optional) | The offset off data result
| limit | Integer | (optional) | The limit number of result

**Return**

List<[AppModel](../model/app/app/app-model)>

**Sample code**

<details class="tab-container" open>
<Summary>get Apps By Space IDs</Summary>

**Source code**

```java  
List<Integer> spaceIds = new List<Integer>();
spaseIds.add({your_space_id});
spaseIds.add({your_space_id});
Integer offset = {your_offset};
Integer limit = {your_litmit};

App appManagerment = new App(connection);
List<AppModel> appList = appManagerment.getAppsBySpaceIDs(spaceIds, offset, limit);
```

</details>

### addPreviewApp(String name, Integer space, Integer thread)

Creates a preview App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| name | String | yes | The App name.<br>The maximum length is 64 characters.|
| space | Integer | (optional) | The Space ID of where the App will be created.|
| thread | Integer | (optional) | The Thread ID of the thread in the Space where the App will be created.<br>It is recommended to ignore this parameter so that Apps are created in the default thread. <br>There is currently no helpful reason to create Apps in threads other than the default thread, as there are no visual representations in kintone of Apps being related to threads.<br> There are only visual representations of Apps being related to Spaces.|

**Return**

[PreviewApp](../model/app/app/preview-app)

**Sample code**

<details class="tab-container" open>
<Summary>add PreviewApp</Summary>

**Source code**

```java  
Integer spaceId = {your_space_id} // Space will add this app
Integer threadId = {your_thread_id} // Thread will add this app

App appManagerment = new App(connection);
appManagerment.addPreviewApp(appName, spaceId, threadId);

```
</details>


### deployAppSettings(Array<PreviewApp> apps, Boolean revert)

Updates the settings of a pre-live App to the live App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| apps | Array<PreviewApp> | yes | The list of Apps to deploy the pre-live settings to the live Apps. The Maximum limit is 300.<br>If Apps are being deployed to Guest Spaces, Apps can only be deployed to the same Guest Space..|
| revert | Boolean | (optional) | Specify <b>"true"</b> to cancel all changes made to the pre-live settings. The pre-live settings will be reverted back to the current settings of the live app.|

**Return**

None

**Sample code**

<details class="tab-container" open>
<Summary>deploy AppSettings</Summary>

**Source code**

```java  
Integer appId = {your_app_id}
Integer revision = {your_revision} // Revision of application to deploy
ArrayList<appPreview> appPreviewList = new ArrayList<appPreview>();
PreviewApp appPreview = new PreviewApp(appId, revision)

App appManagerment = new App(connection);
appManagerment.deployAppSettings(appPreviewList, false)

```

</details>

### getAppDeployStatus(List<Integer> apps)

Updates the settings of a pre-live App to the live App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| apps | List<Integer> | yes | The list of Apps to check the deploy statuses of. The Maximum limit is 300.<br>If Apps in Guest Spaces are specified, all Apps specified in the request must belong to that Guest Space.|

**Return**

[GetAppDeployStatusResponse](../model/app/app/get-app-deploy-status-response)

**Sample code**

<details class="tab-container" open>
<Summary>get App DeployStatus</Summary>

**Source code**

```java  
List<Integer> appIds = new List<Integer>();
appIds.add({your_app_id});
appIds.add({your_app_id});

App appManagerment = new App(connection);
GetAppDeployStatusResponse res = appManagerment.getAppDeployStatus(appIds);
for (int i = 0; i < res.getApp.length; i++) {
    print(res.getApp.get(i));
}
```

</details>


### getFormFields(Integer app, LanguageSetting lang, Boolean isPreview)

Get field of the form in the kintone app

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| appId | Integer | yes | The app ID
| lang | LanguageSetting | (optional) | The language code. Support: <ul><li>DEFAULT: Default language setting of system </li><li>JA: Japanese language setting</li><li>ZH: Chinese language setting</li><li>EN: English language setting</li> |
| isPreview | Boolean | (optional) | Get the app form fields with a [pre-live settings](https://developer.kintone.io/hc/en-us/articles/115005509288).

**Return**

[FormFields](../model/app/form/field/form-fields)

**Sample code**

<details class="tab-container" open>
<Summary>get FormFields</Summary>

**Source code**

```java  
Integer appId = {your_app_id} // Integer
LanguageSetting lang = {language_code} // LanguageSetting .Ex: LanguageSetting.JA
Boolean isPreview = true;

App appManagerment = new App(connection);
FormFields fields appManagerment.getFormFields(appId, lang, isPreview)
```

</details>

### addFormFields(Integer app, HashMap<String, Field> fields, Integer revision)

Adds fields to a form of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| appId | Integer | yes | The app ID
| fields | Map | (optional) | The formFields which will add to form of kintone app <br> *Note:* <br> [String: Field]: <ul><li>Key: The field code of field on kintone app</li><li> Value:  The field settings of form field on kintone app </li> </ul>|
| revision | Boolean | (optional) | Specify the revision number of the settings that will be deployed.<br>The request will fail if the revision number is not the latest revision.<br>The revision will not be checked if this parameter is ignored, or -1 is specified.

**Return**

[BasicResponse](../model/app/basic-response)

**Sample code**

<details class="tab-container" open>
<Summary>add FormFields</Summary>

**Source code**

```java  
Integer appId = {your_app_id} // App Id
String fieldCode = {field_code_string} // Field code of new Field. It must be not as same as any fields in Pre-Live App Setttings
Integer revision = {latest_revision_of_the_settings} // Integer

// Create Radio field instance and set properties
RadioButtonField addNewField = new RadioButtonField(fieldCode)
HashMap<String, OptionData> optionArray = new HashMap<String, OptionData>()
optionArray["1"] = OptionData("1","1")
optionArray["2"] = OptionData("2","2")
optionArray["3"] = OptionData("3","3")
addNewField.setOptions(optionArray)
addNewField.setNoLabel(false)
addNewField.setRequired(true)
addNewField.setLabel("Label Radio")
addNewField.setAlign(AlignLayout.VERTICAL)

// Add Field object into dictionary with key is Field Code
HashMap<String, Field> properties = new HashMap<String, Field>()
properties.put(fieldCode, addNewField);
// Another add field here

App appManagerment = new App(connection);
BasicResponse res = appManagerment.addFormFields(appId, properties, revision);

```

</details>

### updateFormFields(Integer app, HashMap<String, Field> fields, Integer revision)

Updates the field settings of fields in a form of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The app ID
| fields | Map| (optional) | The formFields which will add to form of kintone app <br> *Note:* <br> [String: Field]: <ul><li>Key: The field code of field on kintone app</li><li> Value:  The field settings of form field on kintone app </li> </ul>|
| revision | Boolean | (optional) | Specify the revision number of the settings that will be deployed.<br>The request will fail if the revision number is not the latest revision.<br>The revision will not be checked if this parameter is ignored, or -1 is specified.

**Return**

[BasicResponse](../model/app/basic-response)

**Sample code**

<details class="tab-container" open>
<Summary>update FormFields</Summary>

**Source code**

```java  
Integer appId = {your_app_id} // Integer
String fieldCode = {field_code_string} // String | fieldCode of exist fields in Pre-Live App Setttings
Integer revision = {latest_revision_of_the_settings} // Integer

// Create Field Object to Update
SingleLineTextField updateField = new SingleLineTextField(fieldCode)
updateField.setDefaultValue("Hello Kintone")
updateField.setRequired(true)

// Add Update Field object into dictionary with key is Field Code
HashMap<String, Field> properties = new HashMap<String, Field>()
properties.put(fieldCode, updateField);

App appManagerment = new App(connection);
BasicResponse res = appManagerment.updateFormFields(appId, properties, revision);

```

</details>

### deleteFormFields(Integer app, ArrayList<String> fields, Integer revision)

> Deletes fields from a form of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The app ID
| fields | Array<String\> | yes| The list of field codes of the fields to delete.<br>Up to 100 field codes can be specified.|
| revision | Integer | (optional) | Specify the revision number of the settings that will be deployed.<br>The request will fail if the revision number is not the latest revision.<br>The revision will not be checked if this parameter is ignored, or -1 is specified.

**Return**

[BasicResponse](../model/app/basic-response)

**Sample code**

<details class="tab-container" open>
<Summary>delete FormFields</Summary>

**Source code**

```java  
int appId = {your_app_id} // Integer
ArrayList<String> fieldCodeArray = [{field_code_string}] // Array<String> | Array of fieldCodes of exist fields in Pre-Live App Setttings
int revision = {latest_revision_of_the_settings} // Integer

App appManagerment = new App(connection);
BasicResponse res = appManagerment.deleteFormFields(appId, fieldCodeArray, revision);

```

</details>

### getFormLayout(Integer appId, Boolean isPreview)

Get the layout of form in kintone app

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The kintone app id
| isPreview | Boolean | (optional) | Get the app form layout with a [pre-live settings](https://developer.kintone.io/hc/en-us/articles/115005509288).

**Return**

[FormLayout](../model/app/form/layout/form-layout)

**Sample code**

<details class="tab-container" open>
<Summary>get FormLayout</Summary>

**Source code**

```java  
int appId = {your_app_id} // Integer
boolean isPreview = true

// Get a pre-live (preview) form fields
App appManagerment = new App(connection);
FormLayout res = appManagerment.getFormLayout(appId, isPreview)

```
</details>

### updateFormLayout(Integer app, ArrayList<ItemLayout> layout, Integer revision)

Updates the field layout info of a form in an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | | The kintone app id
| layout | Array<ItemLayout\> | yes | A list of field layouts for each row.
| revision | Integer | (optional) | Specify the revision number of the settings that will be deployed.<br>The request will fail if the revision number is not the latest revision.<br>The revision will not be checked if this parameter is ignored, or -1 is specified.

**Return**

[BasicResponse](../model/app/basic-response)

**Sample code**

<details class="tab-container" open>
<Summary>update FormLayout</Summary>

**Source code**

```java  
int appId = {your_app_id} // Integer
ArrayList<ItemLayout> itemLayoutRequest = new ArrayList<ItemLayout>();
    
// Row Layout
RowLayout rowLayout1 = new RowLayout();
ArrayList<FieldLayout> fieldsRowLayout1: new ArrayList<FieldLayout>();

FieldLayout singleFieldRowLayout1 = new FieldLayout();
singleFieldRowLayout1.setCode("Text");
singleFieldRowLayout1.setType(FieldType.SINGLE_LINE_TEXT.rawValue);
FieldSize singleFieldSizeRowLayout1 = new FieldSize();
singleFieldSizeRowLayout1.setWidth("193");
singleFieldRowLayout.setSize(singleFieldSizeRowLayout1);
fieldsRowLayout1.add(singleFieldRowLayout1!);

FieldLayout richTextFieldRowLayout1 = new FieldLayout();
richTextFieldRowLayout1.setCode("Rich_text");
richTextFieldRowLayout1.setType(FieldType.RICH_TEXT.rawValue);
FieldSize richTextFieldSizeRowLayout1 = new FieldSize();
richTextFieldSizeRowLayout1.setWidth("315")
richTextFieldSizeRowLayout1.setInnerHeight("125")
richTextFieldRowLayout1.setSize(richTextFieldSizeRowLayout1)
fieldsRowLayout1.add(richTextFieldRowLayout1!)

rowLayout1.setFields(fieldsRowLayout1)

// Subtable Layout
SubTableLayout subTableLayout = new SubTableLayout();
ArrayList<FieldLayout> fieldSubTableLayout = new ArrayList<FieldLayout>();

FieldLayout singleFieldSubTableLayout1 = new FieldLayout();
singleFieldSubTableLayout1.setCode("Text_0");
singleFieldSubTableLayout1.setType(FieldType.SINGLE_LINE_TEXT.rawValue);
FieldSize singleFieldSizeSubTableLayout1 = new FieldSize();
singleFieldSizeSubTableLayout1.setWidth("193");
singleFieldSubTableLayout1.setSize(singleFieldSizeSubTableLayout1);

fieldSubTableLayout.add(singleFieldSubTableLayout1!);
subTableLayout.setFields(fieldSubTableLayout);
subTableLayout.setCode("Table");

// GROUP Layout
GroupLayout groupLayout = new GroupLayout();
ArrayList<RowLayout> rowLayoutInGroup = new ArrayList<RowLayout>();
// Row Layout
RowLayout firstRowLayoutInGroup = new RowLayout();
ArrayList<FieldLayout> fieldsInRowLayoutInGroup = new ArrayList<FieldLayout>()
// Numeric Field Layout
FieldLayout numericFieldInRowLayoutInGroup = new FieldLayout();
numericFieldInRowLayoutInGroup.setCode("Number");
numericFieldInRowLayoutInGroup.setType(FieldType.NUMBER.rawValue);
// field size
FieldSize numericFieldSizeInRowLayoutInGroup = new FieldSize();
numericFieldSizeInRowLayoutInGroup.setWidth("200")
numericFieldInRowLayoutInGroup.setSize(numericFieldSizeInRowLayoutInGroup)

fieldsInRowLayoutInGroup.append(numericFieldInRowLayoutInGroup!)
firstRowLayoutInGroup.setFields(fieldsInRowLayoutInGroup)
rowLayoutInGroup.append(firstRowLayoutInGroup!)
groupLayout.setLayout(rowLayoutInGroup)
groupLayout.setCode("Field_group")

// Append layout
itemLayoutRequest.add(rowLayout1!)
itemLayoutRequest.add(subTableLayout!)
itemLayoutRequest.add(groupLayout!)

App appManagerment = new App(connection);
BasicResponse res = appManagerment.updateFormLayout(appId, itemLayoutRequest);

```

</details>

### getGeneralSettings(Integer app, LanguageSetting lang, Boolean isPreview)

Gets the description, name, icon, revision and color theme of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The kintone app id
| lang | LanguageSetting | (optional) | The localized language to retrieve the data in language constants
| isPreview | Boolean | (optional) | Get general settings of the app with a [pre-live settings](https://developer.kintone.io/hc/en-us/articles/115005509288).

**Return**

[GeneralSettings](../model/app/general/general-settings)

**Sample code**

<details class="tab-container" open>
<Summary>get GeneralSettings</Summary>

**Source code**

```java  
int appId = {your_app_id};
LanguageSetting lang = {your_language_code} // LanguageSetting( EN | JA | ZH ). Ex: LanguageSetting.JA
boolean isPreview = true

App appManagerment = new App(connection);
GeneralSettings res = appManagerment.getGeneralSettings(appId, lang, isPreview);

```

</details>

### updateGeneralSettings(Integer app, GeneralSettings generalSettings, Integer revision)

Updates the description, name, icon, revision and color theme of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The kintone app id
| generalSettings | GeneralSettings | (Conditional) | The description, name, icon, revision and color theme of an App.<br>The request will fail if the revision number is not the latest revision.<br>The revision will not be checked if ignored, or -1 is specified.

**Return**

[BasicResponse](../model/app/basic-response)

**Sample code**

<details class="tab-container" open>
<Summary>update general settings</Summary>

**Source code**

```java  
int appId = {your_app_id};

GeneralSettings appGeneralSetting = new GeneralSettings();
appGeneralSetting.setName("GetViewsApp_Test");
appGeneralSetting.setDescription("<div>A list of great places to go!</div>");
Icon iconModel = new Icon("APP39", Icon.IconType.PRESET);
appGeneralSetting.setIcon(iconModel);
appGeneralSetting.setTheme(GeneralSettings.IconTheme.WHITE);

App appManagerment = new App(connection);
BasicResponse res = appManagerment.updateGeneralSettings(appId, appGeneralSetting);

```

</details>

### getViews(Integer app, LanguageSetting lang, Boolean isPreview)

Gets the View settings of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The kintone app id
| lang | LanguageSetting | (optional) | The localized language to retrieve the data in language constants
| isPreview | Boolean | (optional) | Get views of the app with a pre-live settings when isPreview param is set <b>true</b>.

**Return**

[GetViewsResponse](../model/app/view/update-views-response)

**Sample code**

<details class="tab-container" open>
<Summary>get Views</Summary>

**Source code**

```java  
int appId = {your_app_id}
LanguageSetting lang = LanguageSetting.EN // LanguageSetting( EN | JA | ZH ). Ex: LanguageSetting.JA
boolean isPreview = true

App appManagerment = new App(connection);
GetViewsResponse res = app.getViews(appId, lang, isPreview);

```

</details>

### updateViews(Integer app, HashMap<String, ViewModel> views, Integer revision)

Updates the View settings of an App.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| app | Integer | yes | The kintone app id
| views | HashMap<String, View> | yes | An object of data of Views.
| revision | Integer | (optional) | Specify the revision number of the settings that will be deployed.<br>The request will fail if the revision number is not the latest revision.<br>The revision will not be checked if this parameter is ignored, or -1 is specified.


**Return**

[UpdateViewsResponse](../model/app/view/update-views-response)

**Sample code**

<details class="tab-container" open>
<Summary>update Views</Summary>

**Source code**

```java  
int appId = {your_app_id)}
int revision = {your_lastest_revision} //default: revision = -1

HashMap<String, ViewModel> viewEntry = new HashMap<String: ViewModel>();
ViewModel updateViewModel = new ViewModel();
updateViewModel.setName("ViewTest")
updateViewModel.setSort("Record_number desc")
updateViewModel.setType(ViewModel.ViewType.LIST)
updateViewModel.setFilterCond("Created_datetime = LAST_WEEK()")
updateViewModel.setIndex(1)
ArrayList<String> fieldsViews = new ArrayList<String>();
fieldsViews.add("Text");
fieldsViews.add("Text_Area");
fieldsViews.add("Created_datetime");
updateViewModel.setFields(fieldsViews);
viewEntry.put("ViewTest", updateViewModel);

ViewModel updateViewModel2 = new ViewModel();
updateViewModel2.setName("ViewTest2")
updateViewModel2.setSort("Record_number asc")
updateViewModel2.setType(ViewModel.ViewType.LIST)
updateViewModel2.setFilterCond("Created_datetime > LAST_WEEK()")
updateViewModel2.setIndex(0)

ArrayList<String> fieldsInViews2 = new ArrayList<String>();
fieldsInViews2.add("Text_Area");
fieldsInViews2.add("Created_datetime");
updateViewModel2.setFields(fieldsInViews2);

viewEntry.put("ViewTest2", updateViewModel2);

App appManagerment = new App(connection);
UpdateViewsResponse res = appManagerment.updateViews(appId, viewEntry, revision);

```

</details>

## Reference

- [Get App](https://developer.kintone.io/hc/en-us/articles/212494888)
- [Get Apps](https://developer.kintone.io/hc/en-us/articles/115005336727)
- [Get Form fields](https://developer.kintone.io/hc/en-us/articles/115005509288)
- [Add Form fields](https://developer.kintone.io/hc/en-us/articles/115005506868)
- [Update Form fields](https://developer.kintone.io/hc/en-us/articles/115005507788)
- [Delete Form fields](https://developer.kintone.io/hc/en-us/articles/115005341187)

- [Get Form Layout](https://developer.kintone.io/hc/en-us/articles/115005509068)
- [Update Form Layout](https://developer.kintone.io/hc/en-us/articles/115005341427)

- [Add Preview App](https://developer.kintone.io/hc/en-us/articles/115004712547)
- [Deploy App Settings](https://developer.kintone.io/hc/en-us/articles/115004881348)
- [Get App Deploy Status](https://developer.kintone.io/hc/en-us/articles/115004890947)
- [Get Views](https://developer.kintone.io/hc/en-us/articles/115004401787)

- [Update Views](https://developer.kintone.io/hc/en-us/articles/115004880588)

- [Get General Settings](https://developer.kintone.io/hc/en-us/articles/115004811668)
- [Update General Settings](https://developer.kintone.io/hc/en-us/articles/115004868628)