
## Overview

Advance component that displays data in table format with capabilities to support to entity, block, image, table types. With table type it can open another tabulator instance as a new tab.

## Importing the component

```
    import { TabulatorComponent } from '../../../shared/components/tabulator/tabulator.component';

   -------------------------------------
    @Component({
     .....
     imports:[
      .....,
      TabulatorComponent
     ]
 
```

## Implementing the component

```
    <app-tabulator [data]="data" [columns]="columns" [primaryTableRowContextMenuOptions]="primaryTableRowContextMenuOptions"
     (saveDataEvent)="saveDataEvent($event)"></app-tabulator>
```
## API Reference

### Inputs - For every input property, list the following

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `data` | `Array` | `[]` | [Details](#dataInput) |
| `columns` | `Array` | `[]` | [Details](#columnInput) |
| `primaryTableRowContextMenuOptions` | `object` | `{addRowAbove:false,addRowBelow:false,deleteRow:false}` | Details |
| `childTableRowContextMenuOptions` | `object` |  `{addRowAbove:true,addRowBelow:true,deleteRow:true}` | Details |
| `primaryTableColumnContextMenuOptions` | `object` | `{edit:true,insertLeft:true,insterRight:true,delete:true}` | Details |
| `childTableColumnContextMenuOptions` | `object` | `{edit:true,insertLeft:true,insterRight:true,delete:true}` | Details |
| `freezeUptoXRows` | `number` | `0` | Details |
| `freezeUptoXColumns` | `number` | `0` | Details |
| `groupBy` | `string[]` | null | Details |
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
 <a name="dataInput"/>
 
 ## data
 * Description - Table data, either an array object
 * Required  - No

 <a name="columnInput"/>
 
 ## columns 
 * Description - Table column settings, by default an empty object[].Please note, columns must be the same as a key in data array objects.
 * Required  - No
 * Interface -[Column](#columnLink)
 * Usage -
    ```
     columns=[
            {
            title:"Key",
            field:"SSOTKey"
            editor:"input"
            },
            {
            title:"Key",
            field:"SSOTKey"
            editor:"input"
            }
    ]
    ```
  


 ## primaryTableRowContextMenuOptions
* Description - This property will used to add options on right click of row
* Required  - No
* Interface -[RowContextMenuConfig](#rowContextMenuConfig)
* Usage - ``
* Special considerations - 
    | Property | Value | 
    |  --- | --- |
    | `customAction` | `[{label:"Custom Row",action:function(e, row){ row.customEvent();}}]` |


 ## childTableRowContextMenuOptions
  * Description - This property will used to child table add options on right click of row
  * Required  - No
  * Interface -[RowContextMenuConfig](#rowContextMenuConfig)
  * Usage - ``
  * Special considerations - 
      | Property | Value | 
      |  --- | --- |
      | `customAction` | `[{label:"Custom Row",action:function(e, row){ row.customEvent();}}]` |

   ## primaryTableColumnContextMenuOptions
   * Description - This property will used to add options on right click of column header
   * Required  - No
   * Interface -[ColumnContextMenuConfig](#columnContextMenuConfigLink)
   * Usage - ``
   * Special considerations - 
       | Property | Value | 
       |  --- | --- |
       | `customAction` | <pre>[<br>{<br> label:"Hide Column",<br> action:function(e, column){<br> column.hide();<br>  }  <br>}<br>]</pre> |

   ## childTableColumnContextMenuOptions
   * Description - This property will used to child table add options on right click of column header
   * Required  - No
   * Interface -[ColumnContextMenuConfig](#columnContextMenuConfigLink)
   * Usage - ``
   * Special considerations - 
       | Property | Value | 
       |  --- | --- |
       | `customAction` | <pre>[<br>{<br> label:"Hide Column",<br> action:function(e, column){<br> column.hide();<br>  }  <br>}<br>]</pre> |

   ## freezeUptoXRows
   * Description - If you set the `frozenRows` table setup option to an integer value then that many rows of data will be frozen at the top of the table.
   * Required  - No
   * Default Value - `0`
   * Possible Values  - Interger number
     
   ## freezeUptoXColumns
   * Description - You can freeze the position of columns on the left and right of the table using the frozen property.
   * Required  - No
   * Default Value - `0`
   * Possible Values  - Interger number

   ## groupBy
   * Description  -Rows can be grouped by a common field value by setting the groupBy option to the name of the field to be grouped.
   * Required  - No
   * Default Value - '' 
   * Possible Values  - Field name

   ## movableRows
   * Description - If you would prefer the user only be able to move a column around by one particular cell, the you can set the rowHandle property to true in 
                   the column definition object for that column to restrict the trigger for row movement to that cell only.
   * Required  - No
   * Default Value - false
   * Possible Values  - true/false
 
   ## actionMenu
   * Description - This property will used to custom menu left & right side top of the tabulator
   * Required  - No
   * Object - `{left:MenuItem[],right:{edit:boolean,filterLboolean,custom:MenuItem[]}`[link](#headerContextMenu)
   * Default Value - null
   * Usage -
      ```
         actionMenu : ActionMenu:{
             left:[
                 {
                     label:'Menu',
                     items:[
                         {
                              label:'Save',
                             action:()=>{}
                         }
                     ]
                 }
             ],
             right:{
             edit:true,
             filter:true,
             },
         }
      
      ```


## childDocumentId
    * Description - This property will used to child table data save 
    * Required  - No
    * Default Value - ''
       
    
  
    
### Outputs
 ## saveDataEvent
 * Description - The output event emitted by the component
 * Required  - No
       
       

## Interfaces

* [Reference](https://material.angular.io/components/button/api)
##
<a name="rowContextMenuConfig"/> 

 ```
  export interface RowContextMenuConfig {
    addRowAbove: boolean;
    addRowBelow: boolean;
    deleteRow: boolean;
    customActions?: MenuObject<RowComponent>[];
  }
 ```
 *  `MenuObject<RowComponent>[]` - [Reference](https://tabulator.info/docs/5.5/menu#overview-generator)
##

##
<a name="columnLink"/> 

```
  export interface Column {
    title: string;
    field: string;
    hasTabularData?: boolean;
    columns?: Column[];
    editor?: string;
  }
```

##
<a name="columnContextMenuConfigLink"/> 

```
export interface ColumnContextMenuConfig {
  edit: boolean;
  insertLeft: boolean;
  insertRight: boolean;
  delete: boolean;
  customActions?: MenuObject<ColumnComponent>[];
}
```

<a name="rowContextMenuConfig"/> 

```
export interface ActionMenu {
  left: MenuItem[];
  right: {
    edit: boolean;
    filter: boolean;
    custom?: MenuItem[];
  };
}
```
<a name="rowContextMenuConfig"/> 

```
export interface MenuItem {
  label: string;
  items?: MenuItem[];
  icon?: string;
  disabled?: boolean;
  action?: () => void;
}
```


## Constants

* [Reference](https://material.angular.io/components/button/api)

## Child components

* Explain all the sub components of tabulator. Give complete API reference for all of them. Refer to API reference structure above.

### Component 1 - tabulator-table

#### Overview

## Implementing the component
```
    <app-tabulator-table [columns]="columns" [data]="data"
    [rowContextMenuOptions]="primaryTableRowContextMenuOptions"
    [columnContextMenuOptions]="primaryTableColumnContextMenuOptions"
    [freezeUptoXRows]="freezeUptoXRows"
    [freezeUptoXColumns]="freezeUptoXColumns"
    [groupBy]="groupBy"
    [movableColumns]="movableColumns"
    [movableRows]="movableRows"
    [displayFilterInputs]="enableFilter"
    [isEditMode]="isEditMode" [level]="level"
    (tableTypeDoubleClickEvent)="handleTableTypeClickEvent($event)" >
    </app-tabulator-table>
```

#### API Reference

### Inputs - For every input property, list the following

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `data` | `Array` | `[]` | [Details](#dataInput) |
| `columns` | `Array` | `[]` | [Details](#columnInput) |
| `rowContextMenuOptions` | `object` | `{addRowAbove:true,addRowBelow:true,deleteRow:true}` | Details |
| `columnContextMenuOptions` | `object` | `{edit:true,insertLeft:true,insterRight:true,delete:true}` | Details |
| `freezeUptoXRows` | `number` | `0` | Details |
| `freezeUptoXColumns` | `number` | `0` | Details |
| `groupBy` | `string[]` | null | Details |
| `movableRows` | `boolean` | true | Details |
| `movableColumns` | `boolean` | true | Details |
| `displayFilterInputs` | `boolean` | false | Details |
| `isEditMode` | `boolean` | false | Details |
| `level` | `number` | null | Details |


### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `tableTypeDoubleClickEvent` | `Event` | The output event emitted by the component. |

### Property Details (Inputs)

   ## displayFilterInputs
   * Description - Tabulator allows you to filter the table data by any field in the data set.
   * Required  - No
   * Default Value - false

   ## isEditMode
   * Description - Tabulator allow to edit cell value
   * Default Value - false

   ## level 
   * Description - Tabulator number of instance created level
   * Required  - No

## Outputs 

  ## tableTypeDoubleClickEvent
  * Description - The output event emitted by the component. With table type it can open another tabulator instance as a new tab.
    
  

### Component 2 - tabulator-menu

#### Overview 
  Tabulator menu component custom menu option configure  

## Implementing the component
```
    <app-tabulator-menu [leftMenu]="leftMenu" [rightMenu]="rightMenu">
    </app-tabulator-menu>
```
#### API Reference
 
 ### Inputs - For every input property, list the following

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `leftMenu` | `Array` | `[]` | [Details] |
| `rightMenu` | `Array` | `[]` | [Details] |


### Modal Components

### Component 1 - modal

#### Overview
   This modal component will used to create column & update column 
   
#### API Reference
 
 [Reference](https://material.angular.io/components/dialog/overview)
 
 ### Inputs - For every input property, list the following
| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `state` | `string` | `''` | [Details] |

### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `columnAdded` | `Event` | The output event emitted by the component. |


### Component 2 - block-modal

#### Overview
   This modal component will used to update cell value using textarea
   
#### API Reference
 
 [Reference](https://material.angular.io/components/dialog/overview)
 
 ### Inputs - For every input property, list the following
| Property | Type | Default |
| --- | --- | --- |
| `state` | `string` | `''` |
| `rowData` | `object` | `{}` |
| `isView` | `boolean` | `''` |
| `value` | `string` | `''`  |

### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `editCellValue` | `Event` | The output event emitted by the component. |



### Component 3 - image-block-modal

#### Overview
   This modal component will used to update image block 
   
#### API Reference
 
 [Reference](https://material.angular.io/components/dialog/overview)
 
 ### Inputs - For every input property, list the following
| Property | Type | Default |
| --- | --- | --- |
| `columnName` | `string` | `''` |
| `rowData` | `object` | `{}` |
| `isView` | `boolean` | `''` |
| `value` | `string` | `''`  |

### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `deleteCellValue` | `Event` | The output event emitted by the component. |



