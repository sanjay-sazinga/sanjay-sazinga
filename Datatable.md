

## Overview

 create a generic table component that can be used for displaying documents listing, users, clients, roles table, etc

## Importing the component

```
    import { DataTableComponent } from '../../../shared/components/data-table/data-table.component';

   -------------------------------------
    @Component({
     .....
     imports:[
      .....,
      DataTableComponent
     ]
 
```

## Implementing the component

```
    <app-data-table [data]="pagedFiles" [columns]="dataTableColumn"
        [itemsPerPage]="itemsPerPage" [currentPage]="currentPage"
        [customCellBackgoundColor]="customCellBackgoundColor"
        [customCellColor]="customCellColor"
        [customCellClass]="customCellClass"
        [actionButtonHideShow]="actionButtonHideShow"
        [totalItemCounts]="totalItemCounts"
        [isLoading]="isLoading"
        [tableConfiguration]="tableConfiguration"
        (pageChangeClickEvent)="pageChangeClickEvent($event)"
        (changePageSizeClickEvent)="changePageSizeClickEvent($event)"
        (cellClickEvent)="cellClickEvent($event)"
        (actionEvent)="actionEvent($event)"
        (selectedRowIndexEvent)="selectedRowIndexEvent($event)" >
    </app-data-table>
```
## API Reference

### Inputs - For every input property, list the following

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `data` | `Array` | `[]` | [Details](#dataInput) |
| `columns` | `Array` | `[]` | [Details](#columnInput) |
| `tableConfiguration` | `object` | `{}` | Details |
| `totalItemCounts` | `number` | `0` | Details |
| `currentPage` | `number` | `1` | Details |
| `itemsPerPage` | `number` | `10` | Details |
| `groupBy` | `string[]` | null | Details |
| `isLoading` | `boolean` | false | Details |
| `customCellBackgoundColor` | `Event` | null | Details |
| `customCellColor` | `Event` | null | Details |
| `customCellClass` | `Event` | null | Details |
| `actionButtonHideShow` | `Event` | null | Details |


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
