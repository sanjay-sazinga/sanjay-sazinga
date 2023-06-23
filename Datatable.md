

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

