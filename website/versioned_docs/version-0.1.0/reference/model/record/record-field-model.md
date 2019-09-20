---
id: version-0.1.0-record-field-model
title: Field Model
sidebar_label: FieldModel
original_id: record-field-model
---

## FieldValue

General Field's value of the kintone app

### Constructor

**Parameter**

(none)

### Methods

### getType()

> get the type of field.

**Parameter**

(none)

**Return**

FieldType

**Sample code**

<details class="tab-container" open>
<Summary>get the type of field.</Summary>

**Source code**

```java
// execute GET RECORD API
Integer appID = 1;
Integer recordID =1;
GetRecordResponse response = kintoneRecordManager.getRecord(appID, recordID);

HashMap<String, FieldValue> resultRecord = response.getRecord();
FieldValue fv = resultRecord.get("sample field");
FieldType fieldType = fv.getType();
```

</details>

### setType(FieldType type)

> set the type of field.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| type | FieldType  | The type of field - kintone-sdk FieldType constants.

**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the type of field.</Summary>

**Source code**

```java
Integer appID = 1;
HashMap<String, FieldValue> record = new HashMap<String, FieldValue>();

FieldValue fv = new FieldValue();
fv.setType(FieldType.SINGLE_LINE_TEXT);
fv.setValue("sample_AddRecord");
record.put("FieldCode1", fv);

AddRecordResponse response = kintoneRecordManager.addRecord(appID, record);
```

</details>

### getValue()

> get the value of field in the record.

**Parameter**

(none)

**Return**

Object

**Sample code**

<details class="tab-container" open>
<Summary>get the value of field in the record.</Summary>

**Source code**

```java
// execute GET RECORD API
Integer appID = 1;
Integer recordID =1;
GetRecordResponse response = kintoneRecordManager.getRecord(appID, recordID);

HashMap<String, FieldValue> resultRecord = response.getRecord();
FieldValue fv = resultRecord.get("sample field");
Object fieldValue = fv.getValue();
```

</details>

### setValue(Object value)

> set the value of field in the record.

**Parameter**

| Name| type| Description |
| --- | ---  | --- |
| value | Object  | The value of field in the record, read more at [Field Type here](https://developer.kintone.io/hc/en-us/articles/212494818/#responses).


**Return**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>set the value of field in the record.</Summary>

**Source code**

```java
Integer appID = 1;
HashMap<String, FieldValue> record = new HashMap<String, FieldValue>();

FieldValue fv = new FieldValue();
fv.setType(FieldType.SINGLE_LINE_TEXT);
fv.setValue("sample_AddRecord");
record.put("FieldCode1", fv);

AddRecordResponse response = kintoneRecordManager.addRecord(appID, record);
```

</details>

## SubTableValueItem

### Constructor

**Parameter**

(none)

### Methods

### getID()

> get the ID of item in table.

**Parameter**

(none)

**Return**

Integer

**Sample code**

<details class="tab-container" open>
<Summary>get the ID of item in table.</Summary>

**Source code**

```java
// execute GET RECORD API
Integer appID = 1;
Integer recordID =1;
GetRecordResponse response = kintoneRecordManager.getRecord(appID, recordID);

HashMap<String, FieldValue> resultRecord = response.getRecord();
FieldValue fv = resultRecord.get("SubTable field");
Object fieldValue = fv.getValue();
ArrayList<SubTableValueItem> subTable = (ArrayList<SubTableValueItem>)fieldValue;
Integer itemID = subTable.get(0).getID();
```

</details>


### setID(Integer id)

> set the ID of table.

**Parameter**

| Name| type | Description |
| --- | ---  | --- |
| id | Integer | The ID of table .

**Return**

(none)


**Sample code**

<details class="tab-container" open>
<Summary>set the ID of item in table.</Summary>

**Source code**

```java
SubTableValueItem tableItem = new SubTableValueItem();
tableItem.setID(00000);
HashMap<String, FieldValue> tableItemValue = new HashMap<String, FieldValue>();
FieldValue fv1 = new FieldValue();
fv1.setType(FieldType.SINGLE_LINE_TEXT);
fv1.setValue("sample_text1");
FieldValue fv2 = new FieldValue();
fv2.setType(FieldType.SINGLE_LINE_TEXT);
fv2.setValue("sample_text2");
tableItemValue.put("sample field1", fv1);
tableItemValue.put("sample field2", fv2);
tableItem.setValue(tableItemValue);  
```

</details>

### getValue()

> get the value of field in the record.

**Parameter**

(none)

**Return**

HashMap<String, [FieldValue](#fieldvalue)\>

**Sample code**

<details class="tab-container" open>
<Summary>get the ID of item in table.</Summary>

**Source code**

```java
// execute GET RECORD API
Integer appID = 1;
Integer recordID =1;
GetRecordResponse response = kintoneRecordManager.getRecord(appID, recordID);

HashMap<String, FieldValue> resultRecord = response.getRecord();
FieldValue fv = resultRecord.get("SubTable field");
Object fieldValue = fv.getValue();
ArrayList<SubTableValueItem> subTable = (ArrayList<SubTableValueItem>)fieldValue;
HashMap<String, FieldValue> itemValue= subTable.get(0).getValue();
```

</details>

### setValue(HashMap<String, [FieldValue](#fieldvalue)\> value) 

> set the value of field in the record.

**Parameter**

| Name| type | Description |
| --- | ---  | --- |
| value | HashMap<String, [FieldValue](#fieldvalue)\>  | The row data of table.


**Return**

(none)


**Sample code**

<details class="tab-container" open>
<Summary>get the ID of item in table.</Summary>

**Source code**

```java
SubTableValueItem tableItem = new SubTableValueItem();
tableItem.setID(00000);
HashMap<String, FieldValue> tableItemValue = new HashMap<String, FieldValue>();
FieldValue fv1 = new FieldValue();
fv1.setType(FieldType.SINGLE_LINE_TEXT);
fv1.setValue("sample_text1");
FieldValue fv2 = new FieldValue();
fv2.setType(FieldType.SINGLE_LINE_TEXT);
fv2.setValue("sample_text2");
tableItemValue.put("sample field1", fv1);
tableItemValue.put("sample field2", fv2);
tableItem.setValue(tableItemValue); 
```

</details>


