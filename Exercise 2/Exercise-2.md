Exercise 2
================

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0      ✔ purrr   0.3.5 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.5.0 
    ## ✔ readr   2.1.3      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
bikes <- read_csv(
  "https://raw.githubusercontent.com/z3tt/graphic-design-ggplot2/main/data/london-bikes-custom.csv", 
  col_types = "Dcfffilllddddc"
)

bikes$season <- fct_inorder(bikes$season)
bikes_no_na <- na.omit(bikes)

plot_2 <- ggplot(
    data = bikes_no_na,
    aes(x = reorder(weather_type, -count, median), y = count),
  ) +
  geom_boxplot(
    aes(fill = weather_type),
    outlier.shape = NA
  ) +
  geom_jitter(
    width = 0.2,
    height = 0,
    alpha = 0.2,
    aes(color = weather_type)
  ) +
  theme_minimal() +
  labs(
    title = "London Bikeshare Rides by Weather Type",
    y = "Count",
    x = "Weather"
  ) +
  theme(
    legend.position = "none",
    plot.title = element_text(lineheight = 15, face = "bold")
  )

plot_2
```

![](Exercise-2_files/figure-gfm/Exercise%202-1.png)<!-- -->
