
<!-- README.md is generated from README.Rmd. Please edit that file -->
urbnthemes
----------

[![Travis-CI Build Status](https://travis-ci.org/UI-Research/urbnthemes.svg?branch=master)](https://travis-ci.org/UI-Research/urbnthemes)

### Overview

`urbnthemes` is a set of tools for creating Urban Institute-themed plots and maps in R. The package extends `ggplot2` with web, print, and map themes as well as tools that make plotting easier at the Urban Institute. `urbnthemes` replaces the [urban\_R\_theme](https://github.com/UrbanInstitute/urban_R_theme).

### Installation

    install.packages("devtools")
    devtools::install_github("UI-Research/urbnthemes")

### Fonts

The Urban Institute uses [Lato](https://fonts.google.com/specimen/Lato) font for publications. After installing `urbnthemes`, submit `urbnthemes::lato_test()` to see if Lato is imported and registered.

If Lato isn't imported and registered, install [Lato](https://fonts.google.com/specimen/Lato) and then submit `urbnthemes::lato_install()`. If you are on a Windows, you may need to install [ghostscript](https://www.ghostscript.com/download.html) and then submit `Sys.setenv(R_GSCMD = "link to the ghostscript .exe")` before running `urbnthemes::lato_install()`.

Waffle charts with glyphs require fontawesome. `fontawesome_test()` and `fontawesome_install()` are the fontawesome versions of the above functions. Be sure to install fontawesome from [here](https://github.com/hrbrmstr/waffle/tree/master/inst/fonts).

### Usage

``` r
library(ggplot2)
library(urbnthemes)

set_urbn_defaults(style = "print")

ggplot(data = mtcars, mapping = aes(factor(cyl))) +
  geom_bar() + 
  scale_y_continuous(expand = expand_scale(mult = c(0, 0.1))) +
  labs(x = "Number of Cylinders",
       y = "Count") +
  remove_ticks()
```

![](man/figures/README-example-1.png)

``` r
library(ggplot2)
library(urbnthemes)
library(grid)
library(gridExtra)

set_urbn_defaults()

plot <- ggplot(data = mtcars, mapping = aes(factor(cyl))) +
  geom_bar() + 
  scale_y_continuous(expand = expand_scale(mult = c(0, 0.1))) +
  labs(x = "Number of Cylinders",
       y = "Count") +
  remove_ticks()

grid.arrange(plot, urbn_logo_text(), ncol = 1, heights = c(30, 1))
```

![](man/figures/README-example2-1.png)

Core themes:

-   `set_urbn_defaults()`
-   `theme_urbn_web()`
-   `theme_urbn_print()`
-   `theme_urbn_map()`

Formatting functions:

-   `urbn_logo_text()`
-   `remove_ticks()`

Utility functions:

-   `lato_test()`
-   `lato_install()`
-   `fontawesome_test()`
-   `fontawesome_install()`

In development:

-   `urban_logo_image()`
-   `undo_urban_defaults()`
-   `save_urban_print()`
-   `save_urban_web()`
-   `urban_rmarkdown_header()`

### Getting help

Contact [Aaron Williams](awilliams@urban.org) or [Kyle Ueyama](kueyama@urban.org) with feedback or questions.

Code of conduct
---------------

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.
