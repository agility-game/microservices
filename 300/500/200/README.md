# 200 - Functional Data Grid

Based on "Functional Data Grid" at https://github.com/energydrink9/functional-data-grid

This is a library made with React and React-Virtualized for creating rich data grids with filtering, sorting, grouping and aggregates computation. It supports virtualization, and so it can handle very large amounts of data. It features also locked columns, custom renderers, multi-column headers, columns resize, hide / show columns and variable rows height. Filtering, sorting, grouping and aggregates computation are done client-side.

Functional Data Grid is written in functional programming style with ES2016 and Flow. It's really fast and is being used in production with tens of thousands of elements.

## Installation

You can install the library with NPM:

```
$ cd containers/app/webui
$ npm install --save functional-data-grid
```

or with YARN:

```
$ cd containers/app/webui
$ yarn add functional-data-grid
```

## Usage

To use Functional Data Grid, you have to import the library and its base types you intend to use, for example:

```
import React { Component } from 'react';
import FunctionalDataGrid, { Column, Group } from 'functional-data-grid';
...
```
containers/app/webui/src/components/MicroservicesGrid.js

then you can use it inside your `MicroservicesGrid` component. For example:

```
...
let columns = [
    new Column({
      id : 'name',
      title: 'Name',
      width: 300,
      headerStyle: {
        fontSize: 16
      },
      style: {
        fontSize: 16,
        textAlign: 'left'
      }, 
      sortable: true,      
      valueGetter: e => e.name
    }),
    new Column({
      id : 'url',
      title: 'URL',
      width: 200,
      headerStyle: {
        fontSize: 16
      },
      style: {
        fontSize: 16,
        textAlign: 'left'
      },
      sortable: true,    
      valueGetter: e => e.url
    })
  ]

let data = [
    {
      'name': 'Company Purpose',
      'url': '/company-purpose'
    },
    {
      'name': 'Card Charge Worker',
      'url': '/card-charge-worker'
    },
    {
      'name': 'Content Management Systems (CMS)',
      'url': '/cms'
    }
]

let showFooter = false;

class MicroservicesGrid extends React.Component {
  render = () => <FunctionalDataGrid columns={columns} data={data} showFooter={showFooter} />
}

export default MicroservicesGrid
...
```
containers/app/webui/src/components/MicroservicesGrid.js

## Component Props

See https://github.com/energydrink9/functional-data-grid

## Columns Definition

See https://github.com/energydrink9/functional-data-grid

## Groups Definition

See https://github.com/energydrink9/functional-data-grid

## Demo

Check the examples here: https://energydrink9.github.io/functional-data-grid-examples

## Embed in App Js

We can embed the MicroservicesGrid inside the App Js as follows:

```
import MicroservicesGrid from './components/MicroservicesGrid';
...
function App() {
  return (
    <div className="App">
      ...
          <MicroservicesGrid />
      ... 
    </div>     
  );  
}
...
```
containers/app/webui/src/App.js
