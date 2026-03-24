---
icon: lucide/chart-pie
---

# Coxcomb Charts in Dashboards

## Background
ArcGIS Dashboards provides some great charting abilities out of the box. However, the product doesn't yet support some common chart types. A coxcomb chart (aka a polar area chart or rose diagram), is a combination of a pie chart and a bar chart. In a Coxcomb chart, each category is represented by a segment (like a slice of pie), but instead of the angle of the slice varying (as in a pie chart), it's the radius (length of the segment) that changes[^1]. This visualization was originally created by Florence Nightingale to track death tolls during the Crimean War.

![FLorence](https://www.medhakhurana.com/content/images/size/w1000/2024/09/image-1.png){ width=500 }
Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Nightingale-mortality.jpg?ref=medhakhurana.com)

Sometimes people look for a way to add this impressive visualization into an ArcGIS Dashboard. While not currently supported with drag-and-drop configuration, my colleague [Scott Aulen](https://rscotta.github.io/) presented a way to create a Coxcomb chart using Arcade at Dev and Tech Summit 2026[^2].

## Code
``` javascript linenums="1" title="Coxcomb Chart in a Dashboard using Arcade"
//Get values for first category
var cat_1_linearGradient_ID = $datapoint.FID + '_linearGradient1'
var cat_1_hash_linearGradient_ID = '#' + $datapoint.FID + '_linearGradient1'
var cat_1_radialGradient_ID = $datapoint.FID + '_radialGradient1'
var cat_1_hash_radialGradient_ID = '#' + $datapoint.FID + '_radialGradient1'
var cat_1_color = "#4328E7"
var cat_1_measure = $datapoint.Business / 100

//Get values for second category
var cat_2_linearGradient_ID = $datapoint.FID + '_linearGradient2'
var cat_2_radialGradient_ID = $datapoint.FID + '_radialGradient2'
var cat_2_color = "#9654E5"
var cat_2_measure = $datapoint.Capacity / 100

//Get values for third category
var cat_3_linearGradient_ID = $datapoint.FID + '_linearGradient3'
var cat_3_radialGradient_ID = $datapoint.FID + '_radialGradient3'
var cat_3_color = "#FF6283"
var cat_3_measure = $datapoint.Engagement / 100

//Get values for fourth category
var cat_4_linearGradient_ID = $datapoint.FID + '_linearGradient4'
var cat_4_radialGradient_ID = $datapoint.FID + '_radialGradient4'
var cat_4_color = "#FF8800"
var cat_4_measure = $datapoint.Governance / 100

//Get values for fifth category
var cat_5_linearGradient_ID = $datapoint.FID + '_linearGradient5'
var cat_5_radialGradient_ID = $datapoint.FID + '_radialGradient5'
var cat_5_color = "#FFC502"
var cat_5_measure = $datapoint.Systems / 100


return {
  textColor: '',
  backgroundColor: '',
  separatorColor:'#ffffff',
  selectionColor: '',
  selectionTextColor: '',
  attributes: {
    cat_1_linearGradient_ID: cat_1_linearGradient_ID,
    cat_1_hash_linearGradient_ID: cat_1_hash_linearGradient_ID,
    cat_1_radialGradient_ID: cat_1_radialGradient_ID,
    cat_1_hash_radialGradient_ID: cat_1_hash_radialGradient_ID,
    cat_1_color: cat_1_color,
    cat_1_measure: cat_1_measure,
    cat_2_linearGradient_ID: cat_2_linearGradient_ID,
    cat_2_radialGradient_ID: cat_2_radialGradient_ID,
    cat_2_color: cat_2_color,
    cat_2_measure: cat_2_measure,
    cat_3_linearGradient_ID: cat_3_linearGradient_ID,
    cat_3_radialGradient_ID: cat_3_radialGradient_ID,
    cat_3_color: cat_3_color,
    cat_3_measure: cat_3_measure,
    cat_4_linearGradient_ID: cat_4_linearGradient_ID,
    cat_4_radialGradient_ID: cat_4_radialGradient_ID,
    cat_4_color: cat_4_color,
    cat_4_measure: cat_4_measure,
    cat_5_linearGradient_ID: cat_5_linearGradient_ID,
    cat_5_radialGradient_ID: cat_5_radialGradient_ID,
    cat_5_color: cat_5_color,
    cat_5_measure: cat_5_measure

  }
}
HTML

<h2>
  <strong>{field/Organization}</strong>
</h2>
<div style="text-align:center;">
  <svg width="75%" height="auto" viewbox="0 0 999.99998 999.99998">
    <defs id="defs1">
      <lineargradient id="{expression/cat_1_linearGradient_ID}" inkscape:collect="always">
        <stop style="stop-color:{expression/cat_1_color};stop-opacity:1;" offset="{expression/cat_1_measure}" id="stop_1a"></stop>
        <stop style="stop-color:{expression/cat_1_color};stop-opacity:0;" offset="{expression/cat_1_measure}" id="stop_1b"></stop>
      </lineargradient>
      <lineargradient id="{expression/cat_2_linearGradient_ID}" inkscape:collect="always">
        <stop style="stop-color:{expression/cat_2_color};stop-opacity:1;" offset="{expression/cat_2_measure}" id="stop_2a"></stop>
        <stop style="stop-color:{expression/cat_2_color};stop-opacity:0;" offset="{expression/cat_2_measure}" id="stop_2b"></stop>
      </lineargradient>
      <lineargradient id="{expression/cat_3_linearGradient_ID}" inkscape:collect="always">
        <stop style="stop-color:{expression/cat_3_color};stop-opacity:1;" offset="{expression/cat_3_measure}" id="stop_3a"></stop>
        <stop style="stop-color:{expression/cat_3_color};stop-opacity:0;" offset="{expression/cat_3_measure}" id="stop_3b"></stop>
      </lineargradient>
      <lineargradient id="{expression/cat_4_linearGradient_ID}" inkscape:collect="always">
        <stop style="stop-color:{expression/cat_4_color};stop-opacity:1;" offset="{expression/cat_4_measure}" id="stop_4a"></stop>
        <stop style="stop-color:{expression/cat_4_color};stop-opacity:0;" offset="{expression/cat_4_measure}" id="stop_4b"></stop>
      </lineargradient>
      <lineargradient id="{expression/cat_5_linearGradient_ID}" inkscape:collect="always">
        <stop style="stop-color:{expression/cat_5_color};stop-opacity:1;" offset="{expression/cat_5_measure}" id="stop_5a"></stop>
        <stop style="stop-color:{expression/cat_5_color};stop-opacity:0;" offset="{expression/cat_5_measure}" id="stop_5b"></stop>
      </lineargradient>
      <radialgradient inkscape:collect="always" xlink:href="#{expression/cat_1_linearGradient_ID}" id="{expression/cat_1_radialGradient_ID}" cx="499.75" cy="488.14261" fx="499.75" fy="488.14261" r="238.04262" gradienttransform="matrix(1.6972624,1.2331346,-1.2330055,1.6970846,253.67558,-944.67833)" gradientunits="userSpaceOnUse"></radialgradient>
      <radialgradient inkscape:collect="always" xlink:href="#{expression/cat_2_linearGradient_ID}" id="{expression/cat_2_radialGradient_ID}" gradientunits="userSpaceOnUse" gradienttransform="matrix(-0.64829777,1.995252,-1.995043,-0.64822993,1797.8035,-180.68274)" cx="499.75" cy="488.14261" fx="499.75" fy="488.14261" r="238.04262"></radialgradient>
      <radialgradient inkscape:collect="always" xlink:href="#{expression/cat_3_linearGradient_ID}" id="{expression/cat_3_radialGradient_ID}" gradientunits="userSpaceOnUse" gradienttransform="matrix(-2.0979324,-1.0425975e-6,1.1074753e-6,-2.0977127,1548.411,1524.653)" cx="499.75" cy="488.14261" fx="499.75" fy="488.14261" r="238.04262"></radialgradient>
      <radialgradient inkscape:collect="always" xlink:href="#{expression/cat_4_linearGradient_ID}" id="{expression/cat_4_radialGradient_ID}" gradientunits="userSpaceOnUse" gradienttransform="matrix(-0.64829577,-1.9952526,1.9950437,-0.64822782,-150.51898,1813.9795)" cx="499.75" cy="488.14261" fx="499.75" fy="488.14261" r="238.04262"></radialgradient>
      <radialgradient inkscape:collect="always" xlink:href="#{expression/cat_5_linearGradient_ID}" id="{expression/cat_5_radialGradient_ID}" gradientunits="userSpaceOnUse" gradienttransform="matrix(1.6972636,-1.2331329,1.2330037,1.6970859,-950.67934,288.27852)" cx="499.75" cy="488.14261" fx="499.75" fy="488.14261" r="238.04262"></radialgradient>
    </defs>
    <g inkscape:label="Layer 1" inkscape:groupmode="layer" id="layer1">
      <path style="fill:url(#{expression/cat_1_radialGradient_ID});stroke:#a9a9a9;" id="category1" d="M 500,0.4999925 V 500.00001 L 974.9551,345.67774 A 499.5,499.5 0 0 0 793.5078,96.021482 499.5,499.5 0 0 0 500,0.4999925 Z"></path>
      <path style="fill:url(#{expression/cat_2_radialGradient_ID});stroke:#a9a9a9;" id="category2" d="M 975.00392,345.66188 499.95118,500.01587 793.48958,904.03681 A 499.5,499.5 0 0 0 974.85649,654.32214 499.5,499.5 0 0 0 975.00392,345.66188 Z"></path>
      <path style="fill:url(#{expression/cat_3_radialGradient_ID});stroke:#a9a9a9;" id="category3" d="M 793.56853,904.77356 499.96978,500.66956 206.43139,904.69051 a 499.5,499.5 0 0 0 293.53822,95.32409 499.5,499.5 0 0 0 293.59892,-95.24104 z"></path>
      <path style="fill:url(#{expression/cat_4_radialGradient_ID});stroke:#a9a9a9;" id="category4" d="M 205.76224,904.52832 499.36098,500.42436 24.405872,346.1021 a 499.5,499.5 0 0 0 0.0497,308.6282 499.5,499.5 0 0 0 181.306658,249.79802 z"></path>
      <path style="fill:url(#{expression/cat_5_radialGradient_ID});stroke:#a9a9a9;" id="category5" d="m 24.357073,346.08623 475.052707,154.354 -1e-5,-499.39735 A 499.5,499.5 0 0 0 205.90227,96.46151 499.5,499.5 0 0 0 24.35707,346.08622 Z"></path>
      <circle style="fill-opacity:1;fill:none;stroke-dasharray:none;stroke-opacity:0.5;stroke-width:1;stroke:#a9a9a9;" id="category1_outline" cx="500" cy="500" r="499.5"></circle>
      <circle style="fill-opacity:1;fill:none;stroke-dasharray:none;stroke-opacity:0.5;stroke-width:1;stroke:#a9a9a9;" id="category2_outline" cx="500" cy="500" r="374.625"></circle>
      <circle style="fill-opacity:1;fill:none;stroke-dasharray:none;stroke-opacity:0.5;stroke-width:1;stroke:#a9a9a9;" id="category3_outline" cx="500" cy="500" r="249.66678"></circle>
      <circle style="fill-opacity:1;fill:none;stroke-dasharray:none;stroke-opacity:0.5;stroke-width:1;stroke:#a9a9a9;" id="category4_outline" cx="500" cy="500" r="124.75017"></circle>
      <circle style="fill-opacity:1;fill:#ffffff;stroke-dasharray:none;stroke-opacity:0.5;stroke-width:1;stroke:#a9a9a9;" id="category5_outline" cx="500" cy="500" r="25"></circle>
      <text style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;letter-spacing:-0.65px;line-height:1;stroke-dasharray:none;stroke-linejoin:bevel;stroke-opacity:1;stroke-width:1;stroke:none;text-align:center;text-anchor:middle;" xml:space="preserve" x="499.73477" y="15.042881" id="textguide1">
        <tspan style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;" sodipodi:role="line" id="tspan8-9" x="499.40976" y="15.042881">100 </tspan>
      </text>
      <text style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;letter-spacing:-0.65px;line-height:1;stroke-dasharray:none;stroke-linejoin:bevel;stroke-opacity:1;stroke-width:1;stroke:none;text-align:center;text-anchor:middle;" xml:space="preserve" x="500.43311" y="141.28288" id="textguide2">
        <tspan style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;" sodipodi:role="line" id="tspan8-9-5" x="500.10809" y="141.28288">75 </tspan>
      </text>
      <text style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;letter-spacing:-0.65px;line-height:1;stroke-dasharray:none;stroke-linejoin:bevel;stroke-opacity:1;stroke-width:1;stroke:none;text-align:center;text-anchor:middle;" xml:space="preserve" x="500.43311" y="265.2829" id="textguide3">
        <tspan style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;" sodipodi:role="line" id="tspan8-9-5-0" x="500.10809" y="265.2829">50 </tspan>
      </text>
      <text style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;letter-spacing:-0.65px;line-height:1;stroke-dasharray:none;stroke-linejoin:bevel;stroke-opacity:1;stroke-width:1;stroke:none;text-align:center;text-anchor:middle;" xml:space="preserve" x="500.43311" y="389.2829" id="textguide4">
        <tspan style="-inkscape-font-specification:&quot;Avenir Next LT Pro&quot;;fill-opacity:1;fill:#808080;font-family:&quot;Avenir Next LT Pro&quot;;font-size:13.3333px;font-stretch:normal;font-style:normal;font-variant:normal;font-weight:normal;" sodipodi:role="line" id="tspan38" x="500.10809" y="389.2829">25</tspan>
      </text>
    </g>
  </svg>
</div>
```

*Add examples from Dev & Tech of coxcomb in action when avaialble*

[^1]: M. Khurana: ["CoxComb Chart - How do you read and make it?"](https://www.medhakhurana.com/coxcomb-chart-how-to-read-and-make/)
[^2]: The Github repo from this session, which includes the Coxcomb code, can be accessed [here](https://github.com/drozd-j/Unlocking-Config-Apps-DTS-2026/tree/main).