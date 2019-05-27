# ScottPlot

**ScottPlot is an open-source interactive graphing library for .NET written in C#.** 
In a GUI environment ScottPlot makes it easy to display data interactively (left-click-drag pan, right-click-drag zoom). ScottPlot was designed to be fast enough to interactively display large datasets with millions of points (such as WAV files) at high framerates. In non-GUI environments ScottPlot can create graphs and save them as images. ScottPlot is easy to integrate into .NET projects (including cross-platform solutions) because it has no dependencies outside the .NET framework libraries.

![](/demos/ScottPlotDemo/compiled/ScottPlotDemo.gif)

## Quickstart
This quickstart demonstrates how to add an interactive ScottPlot to a Windows Forms Application using the ScottPlotUC (user control).  ScottPlot also has a [Console Application quickstart](/doc/quickstart-console.md) and a [WPF Application quickstart](/doc/quickstart-WPF.md) for those interested in using ScottPlot in other application frameworks. 

* Create a Windows Forms Application
* Add an existing project reference to [ScottPlot.csproj](/src/ScottPlot/ScottPlot.csproj)
* Rebuild the solution
* Drag/Drop the ScottPlotUC (from the toolbox) onto your form
* Add the following code to your startup sequence

```cs
// generate some data to plot
int pointCount = 100;
double[] dataXs = new double[pointCount];
double[] dataSin = new double[pointCount];
double[] dataCos = new double[pointCount];
for (int i = 0; i < pointCount; i++)
{
	dataXs[i] = i;
	dataSin[i] = Math.Sin(i * 2 * Math.PI / pointCount);
	dataCos[i] = Math.Cos(i * 2 * Math.PI / pointCount);
}
```

```cs
// plot the data
scottPlotUC1.plt.PlotScatter(dataXs, dataSin);
scottPlotUC1.plt.PlotScatter(dataXs, dataCos);
scottPlotUC1.plt.XLabel("experiment time (ms)");
scottPlotUC1.plt.YLabel("signal (mV)");
scottPlotUC1.plt.Title("ScottPlot Quickstart");
scottPlotUC1.plt.AxisAuto();
scottPlotUC1.Render();
```

![](/demos/ScottPlotQuickstartForms/compiled/ScottPlotQuickstartForms.png)

Full source code: [demos/ScottPlotQuickstartForms](/demos/ScottPlotQuickstartForms) 

Compiled version: [ScottPlotQuickstartForms.zip](/demos/ScottPlotQuickstartForms/compiled/ScottPlotQuickstartForms.zip)

## Documentation
* The **[ScottPlot Cookbook](/doc/cookbook/README.md)** demonstrates all ScottPlot features
* ScottPlot mouse actions
  * Left-click-drag to pan
  * Right-click-drag to zoom
  * Mouse scroll-wheel to zoom
  * Middle-click for auto-axis
  * Right-click for a dropdown menu
  * Double-click to display benchmark

## Compiled Demos

### ScottPlot Demo
* This demo demonstrates the display all major ScottPlot plot types. Notice that _millions_ of data points can be displayed using a Signal plot at >100 Hz framerates and comfortably interacted with using the mouse.
* Compiled demo: [ScottPlotDemo.zip](/demos/ScottPlotDemo/compiled/ScottPlotDemo.zip)
* Source code: [/demos/ScottPlotDemo/](/demos/ScottPlotDemo/)

![](/demos/ScottPlotDemo/compiled/ScottPlotDemo.png)

### Animated Data
* If you plot a double array with ScottPlot, later updating the original array automatically updates the data in ScottPlot. This simple demo plots an array then uses a timer to update it continuously. Note that the graph is still mouse-interactive (panning and zooming) while continuously updating. 
* Compiled demo: [ScottPlotAnimatedSin.zip](demos/ScottPlotAnimatedSin/compiled/ScottPlotAnimatedSin.zip)
* Source code: [/demos/ScottPlotAnimatedSin/](/demos/ScottPlotAnimatedSin/)

![](demos/ScottPlotAnimatedSin/compiled/ScottPlotAnimatedSin.gif)

### Audio Monitor
* This demo uses two ScottPlot plots to display audio data in real time. The signal (PCM, top) and frequency (FFT, bottom) components are continuously updated at a high framerate and are both mouse-interactive. Audio processing is provided by the [nAudio](https://github.com/naudio/NAudio) library.
* Compiled demo: [ScottPlotAudioMonitor.zip](/demos/ScottPlotAudioMonitor/compiled/ScottPlotAudioMonitor.zip)
* Source code: [/demos/ScottPlotAudioMonitor/](/demos/ScottPlotAudioMonitor/)

![](/demos/ScottPlotAudioMonitor/compiled/ScottPlotAudioMonitor.gif)

## Previous Versions
ScottPlot has improved in performance and simplicity over time. Changes which resulted in a change to the API were compartmentalized into major release versions. It is recommended you use the latest version of ScottPlot for new projects, but all versions can be downloaded for backward-compatibility with existing projects. Each version has its own cookbook demonstrating how to use the API.
* [ScottPlot v3](https://github.com/swharden/ScottPlot/) (May 2019 - present)
* [ScottPlot v2](https://github.com/swharden/ScottPlot/tree/2.1) (Dec 2018 - May 2019)
* [ScottPlot v1](https://github.com/swharden/ScottPlot/tree/1.0) (Jan 2018 - Dec 2018)

## About ScottPlot

ScottPlot was created by [Scott Harden](http://www.SWHarden.com/) of [Harden Technologies, LLC](http://tech.swharden.com). The author of this project may be available for the commissioned creation customized versions of this software which incorporate requested features. Inquiries may be sent to [SWHarden@gmail.com](mailto:swharden@gmail.com).
