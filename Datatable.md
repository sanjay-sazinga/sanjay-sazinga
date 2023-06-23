

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
| `isLoading` | `boolean` | false | Details |
| `customCellBackgoundColor` | `Event` | null | Details |
| `customCellColor` | `Event` | null | Details |
| `customCellClass` | `Event` | null | Details |
| `actionButtonHideShow` | `Event` | null | Details |


### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `cellClickEvent` | `Event` | The output event emitted by the component. |
| `pageChangeClickEvent` | `Event` | The output event emitted by the component. |
| `changePageSizeClickEvent` | `Event` | The output event emitted by the component. |
| `selectedRowIndexEvent` | `Event` | The output event emitted by the component. |
| `mouseEnterEvent` | `Event` | The output event emitted by the component. |
| `mouseLeaveEvent` | `Event` | The output event emitted by the component. |
| `actionEvent` | `Event` | The output event emitted by the component. |

### Property Details (Inputs)
 <a name="dataInput"/>
 
 ## data
 * Description - Table data, either an array object
 * Required  - No

 <a name="columnInput"/>
 
 ## columns 
 * Description - Table column settings, by default an empty object[].Please note, columns must be the same as a key in data array objects.
 * Required  - No
 * Interface - [Column](#columnLink)
 * Usage -
    ```
      dataTableColumn: Column[] = [
    {
      title: 'Status',
      field: 'Status',
      customStyle: true,
      className: 'statuschipblock',
    },
    {
      title: 'DocumentName',
      field: 'DocumentName',
      clickable: true,
      className: 'document-name',
    },
    {
      title: 'Client Name',
      field: 'ClientName',
      orderable: false,
    },
    {
      title: 'Summary',
      field: 'ChildDocStats',
      orderable: false,
      dataType: DataType.array,
      subColumns: ['key', 'count'],
    },
    {
      title: 'Last Updated',
      field: [
        {
          title: 'LastUpdatedBy',
          field: 'LastUpdatedBy',
        },
        {
          title: 'LastUpdatedTimestamp',
          field: 'LastUpdatedTimestamp',
          pipeType: PipeType.date,
          pipeFormat: 'short',
        },
      ],
    },
  ];
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

<a name="columnLink" />

```
export interface Column {
  field: string | Column[];
  title: string;
  width?: string;
  dataType?: DataType;
  subColumns?: string[]; // if data Type array subColumns need
  orderable?: boolean;
  mouseEvent?: boolean;
  headerClass?: string;
  customStyle?: boolean;
  className?: string;
  clickable?: boolean;
  pipeType?: PipeType;
  pipeFormat?: string;
}
```

```
export enum PipeType {
  date = 'date',
}

export enum DataType {
  string = 'string',
  array = 'array',
}
export enum ActionEnum {
  view = 'view',
  delete = 'delete',
  edit = 'edit',
  save = 'save',
  refresh = 'refresh',
  download = 'download',
  restore = 'restore',
  forcedelete = 'forcedelete',
}

```

```
export interface TableConfiguration {
  rowActions?: ActionItem[];
  tableActions?: MenuItem[];
  columnShowHideDropdown?: boolean;
  selectable?: boolean;
  searching?: boolean;
  pagination?: boolean;
  borders?: boolean | Border;
}
```


```
export interface ActionItem {
  icon: string;
  action: ActionEnum;
  title?: string;
  tooltip?: string;
  hide?: boolean;
  permission?: string;
}
```

```
export interface ActionConditionEvent {
  data: any;
  action: string;
}
```

```
export interface ColumnStyle {
  data: any;
  column: string;
}
```

```
export interface TableActionItem {
  action: string;
  row: any;
}
```

```
export interface SelectRowItem {
  selectedAllRows?: boolean;
  selectedRowIndexes?: boolean[];
  selectedRowData?: any;
}
```

```
export interface Border {
  top?: boolean;
  right?: boolean;
  bottom?: boolean;
  left?: boolean;
}
```

```

export interface MenuItem {
  label: string;
  items?: MenuItem[];
  icon?: string;
  disabled?: boolean;
  class?: string;
  action?: () => void;
  permission?: string;
}
```

