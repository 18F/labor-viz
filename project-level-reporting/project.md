# Project Level Reporting

How to create a graph that shows the total hours by employee for a particular project.

Click "Visualize" at the top of Kibana, then choose "Area Chart"
![](1-visualize.png)

The choose "From a new search"
![](2-from-new-search.png)

A blank area chart workspace will appear:
![](3-blank-area-chart-screen.png)

At the top replace "\*" with "project=name" -- this only works for a single word where the word is unique.  If you don't have a unique word in your project you will need to use the project_id.

![](3a-search-project.png)

For the Y-Axis select Aggregation: Sum and Field: hours_spent.
![](4-sum-hours.png)

Next we need to specify buckets!  Select "X-Axis"
![](5a-x-axis-bucket.png)

Choose Aggregation: Date Histogram, Field: start_data, and Interval: Weekly
![](5b-x-axis-data.png)

Next we want to add sub-buckets, of course...
![](5c-add-sub-buckets.png)

For the buckets type, choose "Split Area"
![](5d-split-area.png)

Then select Sub Aggregation: Terms, Field: employee, Order: Top, Size: 50 (make sure this is larger than the number of people on your project), and Order By: metric: Sum of hours_spent
![](5e-terms.png)

Then at the top of the left panel, click the green rectangle with a white arrow to apply the changes:
![](6-apply-changes.png)

Voila!  A graph should appear on the right:
![](7-graph.png)
