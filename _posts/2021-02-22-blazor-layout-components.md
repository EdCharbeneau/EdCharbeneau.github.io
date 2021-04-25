---
layout: post
permalink: /blazor-layout-components/
title: Blazor Layout Components
path: 2021-02-22-blazor-layout-components.md
date: 2021-02-22
tags: 
- Blazor
- CSS Grid
- Flexbox

---

I recently wrote in an article titled "[10 Blazor Features You Probably Didn't Know](https://www.telerik.com/blogs/10-blazor-features-you-probably-didnt-know)" that Blazor can do anything HTML/CSS can do.

> One question that is often asked when approaching Blazor is regarding the use of some user interface framework, CSS library, or specific CSS feature. The answer is a resounding, YES. While Blazor uses Razor templates to create components, the result is HTML rendered in the browser. The HTML and CSS generated by Blazor is no different to the browser than any other HTML or CSS. This means all valid HTML and CSS is valid within a Blazor application. 

I feel that this is something I will be repeating for the foreseeable future as more developer on-board and quickly discover that Blazor is just as much Web as it is .NET. While there are a variety of web frameworks and even [components that help with layout](https://demos.telerik.com/blazor-ui/tilelayout/overview) exist, it's ultimately important to realize that good HTML/CSS knowledge will help. Learning web standards will make these frameworks and tools easier to use and you more effective with them.

Creating layouts on the web has evolved over the years and has gotten much easier as a result. We have seen a progression from HTML `table` elements, to mind boggling CSS `float` trickery, which resulted in a sea of frameworks like Bootstrap. Today modern web development consists of two key CSS features that are all you need to create stunning application layouts: CSS Grid, and Flexbox.

Rather than write about something that has already been covered extensively by the community, we'll break down how each of these features relates to XAML and .NET and where you can find resources to get started. I feel if you take the time to learn CSS Grid and Flexbox, you'll find that application layout in Blazor is much less about Layout Components and more about building a layout with CSS for your Blazor Components to occupy. This should allow you to focus on problem solving with the right tools.

The following examples equate to the [UWP grid layout tutorial]( https://docs.microsoft.com/en-us/windows/uwp/design/layout/grid-tutorial) with web friendly translations.

## CSS Grid

If you're a .NET developer coming from pretty much any background other than the web you can consider CSS Grid the web equivalent of the XAML grid. However, instead of the grid definitions being written inline, CSS will use selectors to target elements on the page.

Below is a snippet of XAML's Grid Layout

```html
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="3*"/>
        <ColumnDefinition Width="5*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="2*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
</Grid>
```

Below is the equivalent CSS code to the XAML markup 

```css
.main-layout {
  display: grid;
  height: 100vh;
  grid-template-columns: 3fr 5fr; /* two columns template */
  grid-auto-rows: 2fr 1fr; /* use auto for infinity */
}
```

Below is the HTML which the CSS is applied to

```html
<div class="main-layout">
    <div>Column three fractions wide, two tall</div>
    <div>Column five fractions wide, two tall</div>
    <div>Column three fractions wide, one tall</div>
    <div>Column five fractions wide, one tall</div>
    <div>Column three fractions wide, two tall</div>
</div>
```

You can see a live example of this in the codepen provided below.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="EdCharbeneau" data-slug-hash="vYyeQJQ" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="vYyeQJQ">
  <span>See the Pen <a href="https://codepen.io/EdCharbeneau/pen/vYyeQJQ">
  vYyeQJQ</a> by EdCharbeneau (<a href="https://codepen.io/EdCharbeneau">@EdCharbeneau</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

This example of course is just the tip of an iceberg and not everything is a clear cut 1:1 translation. Hopefully this is enough to encourage you to learn more about CSS Grid. You can use the following links form the resources below from CSS Tricks to get you acquainted. 

1. [Getting Started with CSS Grid](https://css-tricks.com/getting-started-css-grid/)
2. [Responsive Grid Magazine Layout in Just 20 Lines of CSS](https://css-tricks.com/responsive-grid-magazine-layout-in-just-20-lines-of-css/)
3. [Learning Grid & Flexbox with Kyle Simpson](https://css-tricks.com/video-screencasts/196-learning-grid-flexbox-with-kyle-simpson/)

## CSS Flexbox

Much like the CSS Grid we can draw a similar comparison for XAML's StackPanel another beloved .NET layout tool of many longtime .NET developers. In a modern web application the CSS Flexbox has a striking resemblance to the StackPanel layout.

Below is a snippet of XAML's StackPanel Layout

```xml
<StackPanel Grid.Column="1" Margin="40,0,0,0" VerticalAlignment="Center">
    <TextBlock Foreground="White" FontSize="25" Text="Today - 64° F"/>
    <TextBlock Foreground="White" FontSize="25" Text="Partially Cloudy"/>
    <TextBlock Foreground="White" FontSize="25" Text="Precipitation: 25%"/>
</StackPanel>
<StackPanel Grid.Row="1" Grid.ColumnSpan="2" Orientation="Horizontal"
            HorizontalAlignment="Center" VerticalAlignment="Center">
    <TextBlock Foreground="White" FontSize="25" Text="High: 66°" Margin="0,0,20,0"/>
    <TextBlock Foreground="White" FontSize="25" Text="Low: 43°" Margin="0,0,20,0"/>
    <TextBlock Foreground="White" FontSize="25" Text="Feels like: 63°"/>
</StackPanel>
```

Below is the equivalent CSS code to the XAML markup 

```css
.stack-vertical {
  display:flex;
  flex-direction: column;
  background-color: #34ace0;
  color: white;
  align-items: center;
}

.stack-horizontal {
  display: flex;
  flex-direction: row;
  gap:20px;
  background-color: #227093;
  color: white;
  justify-content: center;
}
```

Below is the HTML which the CSS is applied to

```html
<div class="stack-vertical">
  <p>Today - 64° F</p>
  <p>Partially Cloudy"</p>
  <p>Precipitation: 25%"</p>
</div>
<div class="stack-horizontal">
  <p>High: 66°</p>
  <p>Low: 43°</p>
  <p>Feels like: 63°</p>
</div>
```

You can see a live example of this in the codepen provided below.

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="css,result" data-user="EdCharbeneau" data-slug-hash="ExNwGNd" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="ExNwGNd">
  <span>See the Pen <a href="https://codepen.io/EdCharbeneau/pen/ExNwGNd">
  ExNwGNd</a> by EdCharbeneau (<a href="https://codepen.io/EdCharbeneau">@EdCharbeneau</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

Again, this example of course is just the tip of an iceberg and not everything is a clear cut 1:1 translation. Hopefully this is enough to encourage you to learn more about CSS Flexbox for all your StackPanel needs.

Once again CSS Tricks is my go-to resource for details on Flexbox, their "[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)" article is the only Flexbox resource you'll probably ever need.

## Mixing Grid and Flexbox

Just as XAML allows .NET developers to mix Grid Layouts and StackPanels, so do their web counterparts. In fact, mixing both Grid and Flexbox provides complete set of utilities to describe almost any layout scenario in a Blazor application. Because of this there's no need for a dedicated Blazor Layout Component, since the tools we need are already built into the browser as web standard functionality.

In these examples we'll also use some grid positioning properties `grid-column` and `grid-row` to identify some differences between XAML and CSS. When using HTML/CSS elements generally render to the browser (grid, felxbox, etc.) in their **source order**, or the order in which they are expressed in markup. The opposite holds true for the XAML Grid which interprets no `Grid.Row` or `Grid.Column` property defined to `Grid.Row="0" or Grid.Column="0"`. In CSS Grid each HTML element will render after the next unless coordinates are specified.

Below is a snippet of XAML Grid and StackPanel Layouts

```xml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="3*"/>
        <ColumnDefinition Width="5*"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="2*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Border Background="#2f5cb6"/>
    <Border Grid.Column ="1" Background="#1f3d7a"/>
    <Border Grid.Row="1" Grid.ColumnSpan="2" Background="#152951"/>

<StackPanel Grid.Column="1" Margin="40,0,0,0" VerticalAlignment="Center">
    <TextBlock Foreground="White" FontSize="25" Text="Today - 64° F"/>
    <TextBlock Foreground="White" FontSize="25" Text="Partially Cloudy"/>
    <TextBlock Foreground="White" FontSize="25" Text="Precipitation: 25%"/>
</StackPanel>

<StackPanel Grid.Row="1" Grid.ColumnSpan="2" Orientation="Horizontal"
            HorizontalAlignment="Center" VerticalAlignment="Center">
    <TextBlock Foreground="White" FontSize="25" Text="High: 66°" Margin="0,0,20,0"/>
    <TextBlock Foreground="White" FontSize="25" Text="Low: 43°" Margin="0,0,20,0"/>
    <TextBlock Foreground="White" FontSize="25" Text="Feels like: 63°"/>
</StackPanel>

<Image Margin="20" Source="Assets/partially-cloudy.png"/>

</Grid>
```

In HTML we can markup our code in very similar manner. A grid is used to create the overall layout of the elements, then flexbox is used within the grid cells to describe the flow of the elements within each cell.

Below is the equivalent CSS code to the XAML markup 

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 2fr;
}
.stack-vertical {

  display:flex;
  flex-direction: column;
  background-color: #34ace0;
  color: white;
  justify-content: center;
  align-items: center;
}

.stack-horizontal {
  grid-column: 1 / span 2;
  display: flex;
  flex-direction: row;
  gap:20px;
  background-color: #227093;
  color: white;
  justify-content: center;
}

.weather-symbol {
  /* 
  Items will render to the grid in their 
  source order (order in which they are expressed in markup).
  The opposite holds true with XAML, where no grid column defiend means zero (0,0).
  */
  grid-column: 1 / span 1;
  grid-row: 1 / span 1;
  display: flex;
  font-size:5em;
  background-color: #273c75;
  color: #fbc531;
  justify-content: center;
  align-items: center;
}
```

Below is the HTML which the CSS is applied to

```html
<div class="grid-container">

  <div class="stack-vertical">
    <p>Today - 64° F</p>
    <p>Partially Cloudy"</p>
    <p>Precipitation: 25%"</p>
  </div>

  <div class="stack-horizontal">
    <p>High: 66°</p>
    <p>Low: 43°</p>
    <p>Feels like: 63°</p>
  </div>

  <div class="weather-symbol">
    <p>☀</p>
  </div>
  
</div>
```

You can see a live example of this in the codepen provided below.

<p class="codepen" data-height="423" data-theme-id="dark" data-default-tab="result" data-user="EdCharbeneau" data-slug-hash="NWbaewg" style="height: 423px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="NWbaewg">
  <span>See the Pen <a href="https://codepen.io/EdCharbeneau/pen/NWbaewg">
  NWbaewg</a> by EdCharbeneau (<a href="https://codepen.io/EdCharbeneau">@EdCharbeneau</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## Conclusion

I realize many developers are coming from various .NET backgrounds because Blazor offers .NET in the browser. While Blazor does offer an intuitive component model and the ability to share .NET code, it is still very much rooted in the web. This strong reliance on web standards is what makes Blazor a solid platform. As web standards evolve Blazor will automatically inherit these abilities. When it comes to Blazor Layout Components look no further than CSS Grid and CSS Flexbox. Focus on opportunities to fill in gaps where standard UI components don't exist and [feature rich UI components](https://demos.telerik.com/blazor-ui) truly stand out and save time / development costs.