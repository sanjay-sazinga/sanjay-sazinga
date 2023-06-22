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
| `rowContextMenuOptions` | `object` | `null` | Details |
| `freezeUptoXRows` | `number` | `0` | Details |

### Outputs

The following output events can be subscribed to when using the reusable component:

| Event | Payload Type | Description |
| --- | --- | --- |
| `outputEvent` | `Event` | The output event emitted by the component. |

Property 1 - rowContextMenuOptions

* Description
* Required yes/no
* Schema - Configurability? If menu item is configurable, explain it
* Default Value
* Possible Values
* Usage - code example
* Any other details required
* Special considerations (if any)

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
