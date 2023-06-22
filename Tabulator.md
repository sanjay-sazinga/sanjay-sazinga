## Overview

Advance component that displays data in table format with capabilities to support to entity, block, image, table types. With table type it can open another tabulator instance as a new tab.

## Importing the component

```
    import { TabulatorComponent } from '';
```

## Implementing the component

```
    <app-tabulator [inputProperty]="value" (outputEvent)="handleEvent($event)"></app-tabulator>
```
## API Reference

### Inputs - For every input property, list the following

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `data` | `Array` | `null` | Details |
| `columns` | `Array` | `null` | Details |
| `primaryTableRowContextMenuOptions` | `object` | `{addRowAbove:false,addRowBelow:false,deleteRow:false}` | Details |
| `childTableRowContextMenuOptions` | `object` |  `{addRowAbove:true,addRowBelow:true,deleteRow:true}` | Details |
| `primaryTableColumnContextMenuOptions` | `object` | `{edit:true,insertLeft:true,insterRight:true,delete:true}` | Details |
| `childTableColumnContextMenuOptions` | `object` | `{edit:true,insertLeft:true,insterRight:true,delete:true}` | Details |
| `freezeUptoXRows` | `number` | `0` | Details |
| `freezeUptoXColumns` | `number` | `0` | Details |
| `groupBy` | `object` | null | Details |
| `movableRows` | `boolean` | false | Details |
| `movableColumns` | `boolean` | false | Details |
| `actionMenu` | `object` | null | Details |
| `childDocumentId` | `string ` | null | Details |




### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `saveDataEvent` | `Event` | The output event emitted by the component. |

### Property Details (Inputs)
 ## primaryTableRowContextMenuOptions
* Description - This property will used to add options on right click of row
* Required  - No
* Object -`{addRowAbove:boolean,addRowBelow:boolean,deleteRow:boolean,customAction?:object}`[link](#customAction)
* Usage - ``
* Special considerations - 
  <a name="customAction"></a>
  | Property | Value | 
  |  --- | --- |
  | `customAction` | `[{label:"Custom Row",action:function(e, row){ row.customEvent();}}]` |


 ## childTableRowContextMenuOptions
* Description - This property will used to child table add options on right click of row
* Required  - No
* Object -`{addRowAbove:boolean,addRowBelow:boolean,deleteRow:boolean,customAction?:object}`[link](#customAction)
* Usage - ``
* Special considerations - 
  <a name="customAction"></a>
  | Property | Value | 
  |  --- | --- |
  | `customAction` | `[{label:"Custom Row",action:function(e, row){ row.customEvent();}}]` |

edit:true,insertLeft:true,insterRight:true,delete:true
   ## primaryTableColumnContextMenuOptions
* Description - This property will used to add options on right click of column header
* Required  - No
* Object -`{edit:boolean,insertLeft:boolean,insterRight:boolean,delete?:boolean,customAction?:object}`[link](#headerContextMenu)
* Usage - ``
* Special considerations - 
  <a name="headerContextMenu"></a>
  | Property | Value | 
  |  --- | --- |
  | `customAction` |
   ` [
    {
        label:"Hide Column",
        action:function(e, column){
            column.hide();
        }
    },
]` |  

### Outputs

* Explain all the output properties/emitted events in detail.

## Interfaces

* [Reference](https://material.angular.io/components/button/api)

## Constants

* [Reference](https://material.angular.io/components/button/api)

## Child components

* Explain all the sub components of tabulator. Give complete API reference for all of them. Refer to API reference structure above.

### Component 1 - tabulator-menu

#### Overview

#### API Reference

.
.

### Component 2

#### Overview

#### API Reference

..

### Component 3

#### Overview

#### API Reference

..
