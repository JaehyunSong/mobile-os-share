# Mobile OS Share (2009-2022)

* Last updated: 2022/11/08
* Source: <https://gs.statcounter.com>

## Sample

```r
library(tidyverse)
os_df <- read_csv("mobile_os_share.csv")
```

```r
os_df %>%
  mutate(Etc = 100 - Android - iOS) %>%
  select(ID:iOS, Etc) %>%
  filter(Code == "JP") %>%
  pivot_longer(cols      = Android:Etc,
               names_to  = "OS",
               values_to = "Share") %>%
  mutate(OS = fct_inorder(OS)) %>%
  ggplot(aes(x = Date, y = Share)) +
  geom_line(aes(color = OS), size = 1) +
  geom_point(aes(fill = OS), shape = 21, size = 3, color = "white") +
  guides(fill = "none") +
  labs(x = "Year", y = "Share (%)", color = "",
       title = "Japan") +
  scale_x_continuous(breaks = 2009:2022, labels = 2009:2022) +
  theme_bw(base_size = 12) +
  theme(legend.position    = "bottom",
        panel.grid.minor.x = element_blank())
```

![](sample/SamplePlot1.png)

```r
os_df %>%
  mutate(Etc = 100 - Android - iOS) %>%
  select(ID:iOS, Etc) %>%
  filter(Code == "KR") %>%
  pivot_longer(cols      = Android:Etc,
               names_to  = "OS",
               values_to = "Share") %>%
  mutate(OS = fct_inorder(OS)) %>%
  ggplot(aes(x = Date, y = Share)) +
  geom_line(aes(color = OS), size = 1) +
  geom_point(aes(fill = OS), shape = 21, size = 3, color = "white") +
  guides(fill = "none") +
  labs(x = "Year", y = "Share (%)", color = "",
       title = "South Korea") +
  scale_x_continuous(breaks = 2009:2022, labels = 2009:2022) +
  theme_bw(base_size = 12) +
  theme(legend.position    = "bottom",
        panel.grid.minor.x = element_blank())
```

![](sample/SamplePlot2.png)
