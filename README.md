# PanAndZoomPixelArt
A quick and dirty fork of ZoomAndPan for my own needs. The problem I had with the original code, is that it only allows you to control the zoom via a number multiplier. For zooming into pixel art, I need to specify exact sizes otherwize the pixels get very blurry. 

This fork adds a new property ZoomPercentages that can be set in the constructor of the View like this:

`MainWindow.xaml.cs`
```C#
using System.Diagnostics;
using Avalonia;
using Avalonia.Controls;
using Avalonia.Controls.PanAndZoom;
using Avalonia.Input;
using Avalonia.Markup.Xaml;

namespace AvaloniaDemo
{
    public class MainWindow : Window
    {
        private readonly ZoomBorder? _zoomBorder;

        public MainWindow()
        {
            this.InitializeComponent();
            ZoomBorder1.ZoomPercentages = new double[]{ 0.25, 0.5, 0.75, 1, 1.5, 2 , 3, 4 };
        }
    }
}
```


Now when zooming in and out, it will move up and down the array, starting wherever "1" is added to the array. If there is no "1" in the array, then it will start at index 0. 

If the ZoomPercentages array is not defined, the ZoomAndPan code works exactly as it did before. 

Update [6/7/24]
I also added a new property "SpaceBarPan". When set to true, the space bar is required to be pressed before the ZoomBoarder can be panned. 

## License

PanAndZoom is licensed under the [MIT license](LICENSE.TXT).
