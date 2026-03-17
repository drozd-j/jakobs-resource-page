---
icon: lucide/chart-area
---

# Building Charts with Arcade

Communicative and effective map viewer popups are essential for any good map-centric COTS web app. Configuration specialists are accustomed to utilizing HTML, CSS, and ArcGIS Arcade to extend what's possible out of the box. Arcade isn't limited to just text formatting and conditional logic though - the expression language can be used to create complex chart visualizations from input data directly in the popups.


``` javascript title="Arcade Line Chart"
// calculate past 30 days
var currDate = Now()
var thirDays = DateAdd(currDate, -30, "days")

// create empty dictionary + array for chart
var attributes = {};
var thirFieldInfos = [];

// create FeatureSet for gages
var fs = FeatureSetByRelationshipName($feature, "Gage_Readings");
var thirFs = Filter(fs, 'Time >= @thirDays')

// iterate through gages, pulling stage and time
for (var item in thirFs) {
  var thirStage = item["Stage_ft"];
  if (thirStage < 10000000 && thirStage > -999){
    var thirTimex = Text(item["Time"], "M/DD/YYYY h:mm A");
    attributes[thirTimex] = thirStage;
    Push(thirFieldInfos, thirTimex)
  }
}

return {
  type: "media",
  attributes: attributes,
  title: "",
  mediaInfos: [
    {
      type: "linechart",
      altText: "Line chart showing recorded stream height in feet over the last 30 days.",
      title: "<p style='color:#2C486B;font-weight:300;margin:8px'>Last 30 Days</p>",
      value: {
        fields: thirFieldInfos,
        "colors": [
          [
            44,
            72,
            107
          ]
        ]
      }
    }
  ]
}
```