---
id: version-0.4.0-bulks-exception
title: BulksException
sidebar_label: BulksException
original_id: bulks-exception
---

Handle error responses when using multiple bulk request

## Methods

### getResults()

**Parameter**

(none)

**Return**

ArrayList<Object\>

**Sample code**

<details class="tab-container" open>
<Summary>Get responses if exist error when using multiple bulk request</Summary>

**Source code**

```java
try {
    BulkRequestResponse bulkRequestResponse = record.addAllRecords(appID, records);
} catch (BulksException e) {
    System.out.println(e.getResults());
}

```

</details>