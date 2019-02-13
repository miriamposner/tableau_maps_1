# Make a Map with Tableau

Today, we'll build an interactive, data-rich map with Tableau. As is the case with its data visualization capabilities, Tableau is a powerful tool, but its interface can be a bit confusing. In particular, it's important to place measures and dimensions on the canvas in a particular order -- trust me, I discovered this the hard way after clicking around fruitlessly for hours.

We'll be building a map that shows the home counties of people accused of witchcraft in Scotland in the late sixteenth through mid-eighteenth centuries. You can download the CSV here.

## Open Tableau and connect to your data

As you did before, you'll click on **Connect to text file** (*not* **Connect to Excel file**), because Tableau considers CSVs text files. Select the dataset you downloaded earlier.

Once your data has loaded in, click on the orange **Sheet 1 **button at the bottom of the Tableau window.

![][1]

[1]: images/make-a-map-with-tableau/open-tableau-and-connect-to-your-data.png

## Inspect your data

As you'll recall, Tableau divides your columns into **dimensions** and **measures**, and then further subdivides them into data types (like "text," or "number"). Tableau has done a pretty good job, but there's one field it didn't recognize: in the **Dimensions** pane, **Date** should be classified as a date field, not a text field.

To change it, click on the tiny **Abc** icon to the right of the word **Date**. From the drop-down menu, select (of course!) **Date**. The **Abc** icon will transform into a tiny calendar.

![][2]

[2]: images/make-a-map-with-tableau/inspect-your-data.png

## Build a map

For reasons that I confess aren't entirely clear to me, it really matters in which order you add dimensions and measures to the canvas during this process. So follow along as closely as you can!

**Double-click** first **Latitude** and then **Longitude**. (Do *not use ***Latitude (generated) **or** Longitude (generated)**. We'll talk about what these are in the next tutorial.) 

These field names will appear in the **Rows** and **Columns** panes, respectively. A map will appear on the canvas, containing a single data point. (Apparently the average of the longitude and latitude!)

![][3]

[3]: images/make-a-map-with-tableau/build-a-map.png

## Add points to your map

Let's create a map that shows a point for the home county of each person accused of witchcraft. To do this, drag the **Accused ID** dimension onto the **Detail** button within the **Marks** pane. (Got that? Drop the **Accused ID **onto the** Detail **button.)

(Why the **Accused ID** dimension? It's because each record has a unique Accused ID number, so Tableau will be sure to map each record.)

Now, each record appears on your map! Not bad!

This is probably a good time to mention that you can "grab" your map to move it around by clicking your mouse and holding down the **Shift** key.

![][4]

[4]: images/make-a-map-with-tableau/add-points-to-your-map.png

## Scale the points

Perhaps you'd like the points to grow in size if multiple people originated from that location. For that you'll need a measure. From the **Measures** pane, grab the **Number of Records** measure and drop it on the **Size** button within the **Marks** pane.

(In reality, no location has that many records associated with it, so this isn't hugely illuminating.)

![][5]

[5]: images/make-a-map-with-tableau/scale-the-points.png

## Format your tooltip (1)

As you've navigated your map, you may have noticed that **tooltips** -- little information boxes -- appear as you hover over points. However, at the moment, the tooltips aren't as informative as they might be, since they just include latitude, longitude, and an ID number.

There are two steps to creating tooltips. First, for each field you'd like to appear in the tooltip, drag the name and drop it on the **Tooltip** button within the **Marks** pane.

For example, if I want each person's **First Name** to appear in the tooltip, I'll drag that dimension over to the **Tooltip** button.

Do the same for each field you'd like to see in the tooltip.

![][6]

[6]: images/make-a-map-with-tableau/format-your-tooltip--1-.png

## Format your tooltip (2)

Now each of those fields appears in your tooltip when you hover over a point. However, you may want to neaten it up a bit. To do that, click on the **Tooltip** button.

You can delete the fields you don't want to appear, like latitude and longitude. You can also rearrange things as you like. If you accidentally delete something, click on the **Insert** button within the tooltip pop-up window to re-insert it. When you're done, click **OK**.

![][7]

[7]: images/make-a-map-with-tableau/format-your-tooltip--2-.png

## Group points by color

If you have several categories in your data, you might use color to distinguish among them. Our records include data for **Sex**, so we can use color to easily see points for men versus women.

To do that, drag the **Sex** dimension to the **Color** button within the **Marks **pane.

If you then click on the **Colors** button, you'll find that you can alter the colors Tableau uses by default.

![][8]

[8]: images/make-a-map-with-tableau/group-points-by-color.png

## Filter points (1)

Sometimes it's helpful to look at only some data, rather than all of it at once. This can be especially useful when you're trying to explore a dataset. Let's filter by date. There are several parts to this, mostly because of the way that Tableau treats dates.

First, drag the **Date** dimension to the **Filter** pane.

![][9]

[9]: images/make-a-map-with-tableau/filter-points--1-.png

## Filter points (2)

A popup window will ask you how you want to filter on dates. We want to use years, so select **Years**. 

In the next popup window, select **All** (to indicate that we want to use all the years in our filter) and press **OK**.

![][10]

[10]: images/make-a-map-with-tableau/filter-points--2-.png

## Filter points (3)

In the **Filters** pane, you now have a **YEAR(Date) **dimension. Click on it to produce a drop-down menu. From that menu, select **Continuous**.

Why continuous? As you'll see in the next step, we want Tableau to treat dates not individually but as a flowing range of values.

![][11]

[11]: images/make-a-map-with-tableau/filter-points--3-.png

## Filter points (4)

After you select **Continuous,** a popup box will allow you to use scrubbers to define a date range.

![][12]

[12]: images/make-a-map-with-tableau/filter-points--4-.png

## Save/publish your map

Now you can save and publish your map by clicking on **File** and then **Save to Tableau Public.**

![][13]

[13]: images/make-a-map-with-tableau/save-publish-your-map.png