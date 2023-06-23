

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
    className: 'status',
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
  
  ## totalItemCounts
   * Description - This property will used to table number of records 
   * Required  - No
   * Default Value - `0`
   * Possible Values  - Interger number

 ## currentPage
   * Description - This property will used to pagination active page 
   * Required  - No
   * Default Value - `1`
   * Possible Values  - `Interger number`

 ## itemsPerPage
   * Description -  This property will used to how much records on display on table 
   * Required  - No
   * Default Value - `10`
   * Possible Values  - `Interger number`

   ## isLoading
   * Description - This property will used to loader 
   * Required  - No
   * Default Value - `false`
   * Possible Values  - `true/false`


 ## tableConfiguration
* Description -  Table configuration rowaction,tableaction etc...
* Required  - No
* Interface -[TableConfiguration](#tableConfiguration)
* Usage -
   ```
    tableConfiguration: TableConfiguration = {
             rowActions: [
               {
                 icon: 'fas fa-eye',
                 action: ActionEnum.view,
                 tooltip: 'documents.redigitize file',
                 permission: this.appPermissions.VIEW_DOCUMENTS,
               },
               .....
             ],
             tableActions: [
               {
                 label: 'DELETE FILES',
                 icon: 'fas fa-ban',
                 disabled: true,
                 class: 'btn deletebutton',
                 permission: this.appPermissions.DELETE_DOCUMENTS,
                 action: () =>
                   this.confirmAndDeleteMultipleFiles(this.selectedFileIndexes),
               },
             ],
           selectable: true, //show checkbox on table
           pagination: true,
           borders: {
             bottom: true,
             top: true,
           },
           searching: false, ///filter textbox  display
       };
   ```

### Callback Input functions 
 
## customCellBackgoundColor
* Description -   This property will used to apply cell backgound color as per condition  
* Required  - No
* Return Value  - string only
* Usage -
```
customCellBackgoundColor = (file: ColumnStyle): void => {
const column = file?.column;
if (column == 'Status') {
const statusData = this.allDocumentStatuses[file?.data?.Status];
if (statusData) {
 return statusData.background;
}
}
.....
};
```

## customCellColor
* Description -   This property will used to apply cell text color  as per condition  
* Required  - No
* Return Value  - string only
* Usage -
 ```
  customCellColor = (file: ColumnStyle): void => {
   const column = file?.column;
   if (column == 'Status') {
     const statusData = this.allDocumentStatuses[file?.data?.Status];
     if (statusData) {
       return statusData.color;
     }
   }
   .....
  };
```

## customCellClass
* Description -   This property will used to apply cell class as per condition  
* Required  - No
* Return Value  - string only
* Usage -
 ```
   customCellClass = (file: ColumnStyle) => {
     const column = file?.column;
     if (column == 'DocumentName') {
       return file?.data?.isDeleted ? 'deletedFiles' : 'cell-click';
      }
       ....
     };
  
```

## actionButtonHideShow
* Description -   This property will used to use table row action column button hide/show
* Required  - No
* Return Value  - true/false
* Usage -
 ```
      onActionButtonHideShow = (args: ActionConditionEvent) => {
           switch (args?.action) {
              case ActionEnum.view:
                return (
                  args.data.Status != 'Digitization Failed' &&
                  args.data.Status != 'In Process' &&
                  args.data.Status != 'In Queue' &&
                  args.data.Status != 'New'
                );
              case ActionEnum.delete:
                return (
                  this.userService.checkValidComponent('delete-documents') &&
                  !args.data.isDeleted
                );
              case ActionEnum.restore:
                return (
                  this.userService.checkValidComponent('restore-documents') &&
                  args.data.isDeleted
                );
              case ActionEnum.forcedelete:
                return (
                  this.userService.checkValidComponent('delete-documents') &&
                  args.data.isDeleted
                );
              case ActionEnum.download:
                return (
                  this.userService.checkValidComponent('download-digitized') &&
                  args.data.Status !== 'New' &&
                  args.data.Status !== 'In Queue' &&
                  args.data.Status !== 'Digitization Failed' &&
                  args.data.Status !== 'In Process'
                );
              default:
                return true;
             }
        };
  
  ```
 
       
    
  
    
### Outputs
 
 ## cellClickEvent
 * Description -  This output function will used to use table cell click action in column `clickable:true` then only cell click event 
 * Required  - No
 * Usage -
 ```
   openFile(file: ColumnStyle) {
      try {
        const data=file?.data; //In this data property row data
        const field = file?.column;
        if (field == 'DocumentName') {
           // TODO code 
        }
      } catch {       
      }
   }
 ```

 ## pageChangeClickEvent
  * Description -  This output function will used to use table page change 
  * Required  - No // if you need API call do Yes
  * Usage -
  ```
    pageChangeClickEvent(page:number) {
       try {
        // page 
       } catch {       
       }
    }
  ```

 ## changePageSizeClickEvent
  * Description -  This output function will used to use table page size 
  * Required  - No // if you need API call do Yes
  * Usage -
  ```
    changePageSizeClickEvent(pageSize:number) {
       try {
        // pageSize 
       } catch {       
       }
    }
  ```

  ## selectedRowIndexEvent
  * Description -  This output function will used to use table selecting multiple rows
  * Required  - No // if you need selected data the YES
  * Usage -
  ```
     selectedRowIndexEvent(event: SelectRowItem) {
       const selectedRowIndexes = event.selectedRowIndexes;
       const selectedAllRows = event.selectedAllRows;
       // TODO code
     }
  ```

  ## actionEvent
  * Description -  This output function will used to table row action buttons click evrnt
  * Required  - No // if you need action then YES
  * Usage -
  ```
   actionEvent(event: TableActionItem) {
     const data = event.row;
        switch (event.action) {
           case ActionEnum.view: {
             this.viewProcessedDocument(
               'documents/summary',
               event.row._id,
               event.row.DocumentName
             );
             break;
           }       
        }  
     }
  ```

  ## mouseEnterEvent
  * Description -  This output function will used to table column input `mouseEvent:true` then only mouseEnterEvent
  * Required  - No
  * Usage -
  ```
    mouseEnterEvent({data,column}) {
    // TODO
    }
  ```

  ## mouseLeaveEvent
  * Description -  This output function will used to table column input `mouseEvent:true` then only mouseLeaveEvent
  * Required  - No
  * Usage -
  ```
    mouseLeaveEvent({data,column}) {
    // TODO
    }
  ```
       
       

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


### Component 2 - data-table-menu

#### Overview 
  Table menu component custom menu option buttons  

## Implementing the component
```
    <app-data-table-menu [menus]="tableActionMenu" />
```
#### API Reference
 
 ### Inputs - For every input property, list the following

| Property | Type | Default | Description |
| --- | --- | --- | --- |
| `menus` | `Array` | `[]` | [Details] |


#### Custom Pipe

## customPipe 

#### Overview 
  Create a custom pipe for cell value transform ex. date,etc...
  each and every column will pass pipeType & pipeFomrat, pipeType it used for if condition

  ## Exp
  ```
   ....
   {
    title: 'LastUpdatedTimestamp',
    field: 'LastUpdatedTimestamp',
    pipeType: PipeType.date,
    pipeFormat: 'short',
   },
   ....
  ```



