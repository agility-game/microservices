# 100 - Sankey Diagram

Based on "Sankey Diagram" at https://developers.google.com/chart/interactive/docs/gallery/sankey

Based on "How to create Sankey Diagram in React with Google Charts" at https://www.positronx.io/how-to-create-sankey-diagram-in-react-with-google-charts/

Sankey diagrams are best used for showing a flow from one set of values to another. Ideally, in Sankey diagrams, the width of the arrows is proportional to the flow rate.

Ordinarily, this much we know, but do you know how to create a Sankey chart in React application.

If your answer is no, then this tutorial is exclusively for you. In this guide, we will show you how to create a Sankey diagram in React app step by step.

We will use React Google chart library to build the Sankey chart. Also, we will address how to depict static data in Sankey diagrams in React application.

## React JS Sankey Diagram Example

- Step 1: Generate React App (Already done, skip)
- Step 2: Install Google Charts Package
- Step 3: Add Bootstrap Plugin
- Step 4: Create Sankey Diagram Component
- Step 5: Update App Js
- Step 6: Start React App

## Step 1: Generate React App

== We already have the React App, so we can skip this step ==

If you don’t have the React project ready, then worry not. The given below command will help you generate a brand new React app on your machine.

You can use create-react-app and npx to build your first React project.

```
$ cd containers/app
$ npx create-react-app webui
```

Now, step into the webui folder.

```
$ cd webui
```

## Step 2: Install Google Charts Package

Google charts services can be used in React environment, there is a separate library available for React.

Here is the command that you have to type and execute from the terminal window to add the React Google charts package.

```
$ npm install --save react-google-charts
```

## Step 3: Add Bootstrap Plugin

In this step, we are adding the Bootstrap plugin in React.

However, this package is not mandatory; we are propelling this package in our React project only to cut the time we will spend on UI creation.

```
$ npm install --save bootstrap
```

Bootstrap library has been added to React, but that’s not all.

You have to import the bootstrap CSS in App.js file. In this way, bootstrap UI is available throughout the React app.

```
import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
```

## Step 4: Create Sankey Diagram Component

This is the most significant step of this tutorial, in the below code example we will show you how to build the Sankey diagram or chart in React.

First, you need to create the `components` directory, then also create `SankeyChart.js` file.

As soon as you complete the formalities, make sure to add the given code in the new chart component file.

Update components/SankeyChart.js file.

```
import React, { Component } from 'react'
import Chart from 'react-google-charts'

const sankeyData = [
  ['From', 'To', 'Weight'],
  ['Agility Game Microservices', 'Company Purpose', 1],
  ['Agility Game Microservices', 'Charge Card Worker', 1],
  ['Agility Game Microservices', 'Content Management Systems (CMS)', 1],
]

const sankeyOptions = {
  width: 600,
  height: 350,
  sankey: {
    node: {
      label: {
        fontSize: 18
      },
      width: 8,
      interactive: true
    }
  }
}

class SankeyChart extends Component {
  render() {
    return (
      <div className="container mt-5">
        <h2>Agility Game Microservices</h2>
        <Chart
          width={700}
          height={'350px'}
          chartType="Sankey"
          loader={<div>Loading Chart</div>}
          data={sankeyData}
          rootProps={{ 'data-testid': '1' }}
        />
      </div>
    )
  }
}

export default SankeyChart
```

## Step 5: Update App Js

In React, the main component is the App js file, if you want to show the Sankey diagram in React, register the new Sankey component in App.js file.

```
import React from 'react'
import '../node_modules/bootstrap/dist/css/bootstrap.min.css'
import SankeyChart from './components/SankeyChart'
function App() {
  return (
    <div className="App">
      <SankeyChart />
    </div>
  )
}
export default App
```
containers/app/webui/src/App.js

## Step 6: Start React App

We have completed everything related to this tutorial.

Ultimately, the time has come for running the React app and checking the chart on the browser.

```
$ cd containers/app/webui/
$ npm start
```

## Conclusion

Google charts offer a wide array of charts and diagrams if you are a developer and don’t know how to create charts quickly. Fret not; Google’s extensive collection of charts API may solve your tedious problem within seconds.

In this tutorial, we tried to explain how to create the Sankey diagram in React using the React Google chart package. We believe this guide will help you in developing a new type of chart in React.
