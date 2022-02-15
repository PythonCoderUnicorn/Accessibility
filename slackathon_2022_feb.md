
# Slackathon

For this weeks slackathon we will check descriptions in BrailleR for plots from ggplot. Some examples are here:

https://r-resources.massey.ac.nz/BrailleRInAction/GGPlot.html

Jonathan has noticed that some `geom_*` layers do not offer text when used in the BrailleR package. Some examples are `geom_ribbon()` and `ggfortify::autoplot()`.

Please include geom_* and description below:


## Zane's workflow

### Part 1 is the code examples in the book referenced above:

```
# BrailleR package and ggplot2

library(tidyverse)
# install.packages('BrailleR')
library(BrailleR)

# chapter 10 

set.seed(1410)

diamond_sample = diamonds[ sample(nrow(diamonds), 100), ]

p11a = qplot(carat, price, data = diamonds)   # from the book
p11a

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'carat' with labels 0, 1, 2, 3, 4 and 5.
# It has y-axis 'price' with labels 0, 5000, 10000 and 15000.
# The chart is a set of 53940 points.

VI(p11a) # from the book, same output as above

# from the book
ds = qplot(data= diamond_sample, x= carat, y= price, color = color)

ds %>% VI()


# ----- my version
diamond_sample %>% 
  ggplot(
    aes(x= carat,
        y= price,
        col= color)
  )+
  geom_point()+
  ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'carat' with labels 0.5, 1.0, 1.5 and 2.0.
# It has y-axis 'price' with labels 0, 5000, 10000 and 15000.
# There is a legend indicating colour is used to show color, with 7 levels:
# D shown as very deep purple colour, 
# E shown as vivid purplish blue colour, 
# F shown as moderate blue colour, 
# G shown as vivid bluish green colour, 
# H shown as brilliant green colour, 
# I shown as vivid yellow green colour and 
# J shown as vivid greenish yellow colour.
# The chart is a set of 100 points.





# --- add shape
diamond_sample %>% 
  ggplot(
    aes(x= carat,
        y= price,
        col= color,
        shape= cut   # new argument
        ) 
  )+
  geom_point()+
  ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'carat' with labels 0.5, 1.0, 1.5 and 2.0.
# It has y-axis 'price' with labels 0, 5000, 10000 and 15000.
# There is a legend indicating colour is used to show color, with 7 levels:
# D shown as very deep purple colour, 
# E shown as vivid purplish blue colour, 
# F shown as moderate blue colour, 
# G shown as vivid bluish green colour, 
# H shown as brilliant green colour, 
# I shown as vivid yellow green colour and 
# J shown as vivid greenish yellow colour.
# There is a legend indicating shape is used to show cut, with 5 levels:
# Fair shown as solid circle shape, 
# Good shown as solid triangle shape, 
# Very Good shown as solid square shape, 
# Premium shown as plus shape and 
# Ideal shown as boxed X shape.
# The chart is a set of 100 points.




# ----- categorical variable

diamond_sample %>% 
  ggplot(
    aes(x= color,
        y= price/carat,
        col= color,
        geom= 'jitter'   # new argument
    ) 
  )+
  geom_point()+
  ggdark::dark_mode()


qplot(x= color, y=price / carat, data = diamonds, col= color, geom = "jitter")+ ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'color' with labels D, E, F, G, H, I and J.
# It has y-axis 'price/carat' with labels 5000, 10000 and 15000.
# There is a legend indicating colour is used to show color, with 7 levels:
# D shown as very deep purple colour, 
# E shown as vivid purplish blue colour, 
# F shown as moderate blue colour, 
# G shown as vivid bluish green colour, 
# H shown as brilliant green colour, 
# I shown as vivid yellow green colour and 
# J shown as vivid greenish yellow colour.
# The chart is a set of 53940 points.
# These are offset by added random noise, and sorted by color.

```


### Part 2 : going through ggplot geom_*

```
huron <- data.frame(year = 1875:1972, level = as.vector(LakeHuron))
h = ggplot( huron, aes(year))

#------------ geom_ribbon & line
huron %>% 
  ggplot( aes(year))+
  geom_ribbon( aes(ymin= 0, ymax= level))+
  # geom_line()+
  ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'year' with labels 1875, 1900, 1925, 1950 and 1975.
# It has y-axis '' with labels 0, 200, 400 and 600.
# The chart is a ribbon graph that VI can not process.


h +
  geom_ribbon(aes(ymin = level - 1, ymax = level + 1), fill = "grey70") +
  geom_line(aes(y = level))+ ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'year' with labels 1875, 1900, 1925, 1950 and 1975.
# It has y-axis 'level' with labels 575.0, 577.5, 580.0 and 582.5.
# It has 2 layers.
# Layer 1 is a ribbon graph that VI can not process.
# Layer 1 has fill set to light gray.
# Layer 2 is a set of 1 line.
# Line 1 connects 98 points.




# ----- geom_bar()

g <- ggplot(mpg, aes(class, fill= class))
# Number of cars in each class:
g + geom_bar() + ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'class' with labels 2seater, compact, midsize, minivan, pickup, subcompact and suv.
# It has y-axis 'count' with labels 0, 20, 40 and 60.
# There is a legend indicating fill is used to show class, with 7 levels:
# 2seater shown as strong reddish orange fill, 
# compact shown as strong yellow fill, 
# midsize shown as vivid yellowish green fill, 
# minivan shown as brilliant green fill, 
# pickup shown as brilliant blue fill, 
# subcompact shown as vivid violet fill and 
# suv shown as deep purplish pink fill.
# The chart is a bar chart with 7 vertical bars.
# Bar 1 is centered horizontally at 2seater, and spans vertically from 0 to 5 with fill colour strong reddish orange which maps to class = 2seater.
# Bar 2 is centered horizontally at compact, and spans vertically from 0 to 47 with fill colour strong yellow which maps to class = compact.
# Bar 3 is centered horizontally at midsize, and spans vertically from 0 to 41 with fill colour vivid yellowish green which maps to class = midsize.
# Bar 4 is centered horizontally at minivan, and spans vertically from 0 to 11 with fill colour brilliant green which maps to class = minivan.
# Bar 5 is centered horizontally at pickup, and spans vertically from 0 to 33 with fill colour brilliant blue which maps to class = pickup.
# Bar 6 is centered horizontally at subcompact, and spans vertically from 0 to 35 with fill colour vivid violet which maps to class = subcompact.
# Bar 7 is centered horizontally at suv, and spans vertically from 0 to 62 with fill colour deep purplish pink which maps to class = suv.
# These are stacked, as sorted by class.






# --------- geom_col

diamond_sample %>% 
  ggplot( aes(x= price,
              y= cut))+
  scale_x_continuous(labels = scales::comma_format())+
  geom_col()+ ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'price' with labels 0, 50,000, 100,000 and 150,000.
# It has y-axis 'cut' with labels Fair, Good, Very Good, Premium and Ideal.
# The chart is a bar chart with 100 vertical bars.




# ---------- geom_2d

d <- ggplot(diamonds, aes(x, y)) + xlim(4, 10) + ylim(4, 10)
d + geom_bin_2d()+ ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'x' with labels 4, 6, 8 and 10.
# It has y-axis 'y' with labels 4, 6, 8 and 10.
# In this chart fill is used to show count. The legend that would normally indicate this has been hidden.
# The chart is a tile graph that VI can not process.







# ------------- geom_boxplot
p <- ggplot(mpg, aes(class, hwy))
p + geom_boxplot()+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'class' with labels 2seater, compact, midsize, minivan, pickup, subcompact and suv.
# It has y-axis 'hwy' with labels 20, 30 and 40.
# The chart is a boxplot comprised of 7 boxes with whiskers.
# There is a box at x=2seater.
# It has median 25. The box goes from 24 to 26, and the whiskers extend to 23 and 26.
# There are 0 outliers for this boxplot.
# There is a box at x=compact.
# It has median 27. The box goes from 26 to 29, and the whiskers extend to 23 and 33.
# There are 4 outliers for this boxplot.
# There is a box at x=midsize.
# It has median 27. The box goes from 26 to 29, and the whiskers extend to 23 and 32.
# There are 0 outliers for this boxplot.
# There is a box at x=minivan.
# It has median 23. The box goes from 22 to 24, and the whiskers extend to 21 and 24.
# There are 1 outliers for this boxplot.
# There is a box at x=pickup.
# It has median 17. The box goes from 16 to 18, and the whiskers extend to 15 and 20.
# There are 4 outliers for this boxplot.
# There is a box at x=subcompact.
# It has median 26. The box goes from 24.5 to 30.5, and the whiskers extend to 20 and 36.
# There are 2 outliers for this boxplot.
# There is a box at x=suv.
# It has median 17.5. The box goes from 17 to 19, and the whiskers extend to 14 and 22.
# There are 8 outliers for this boxplot.




# NO TEXT OUTPUT 
# -------------- geom_contour
v <- ggplot(faithfuld, aes(waiting, eruptions, z = density))
v + geom_contour()+ggdark::dark_mode()

# no text

ggplot(faithful, aes(waiting, eruptions)) +
  geom_density_2d(z = density)+ggdark::dark_mode()

# no text 

v + geom_contour_filled( aes(z = density))+ggdark::dark_mode()
#  no text

# -----------------------------



# -------- geom_dotplot
ggplot(mtcars, aes(x = mpg)) +
  geom_dotplot()+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'mpg' with labels 10, 15, 20, 25, 30 and 35.
# It has y-axis 'count' with labels 0.00, 0.25, 0.50, 0.75 and 1.00.
# The chart is a dotplot graph that VI can not process.



# ------ geom_hex
d <- ggplot(diamonds, aes(carat, price))
d + geom_hex()+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'carat' with labels 0, 1, 2, 3, 4 and 5.
# It has y-axis 'price' with labels 0, 5000, 10000 and 15000.
# In this chart fill is used to show count. The legend that would normally indicate this has been hidden.
# The chart is a hex graph that VI can not process.




# ---------- geom_histogram
ggplot(diamonds, aes(carat)) +
  geom_histogram(binwidth = 0.01)+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'carat' with labels 0, 1, 2, 3, 4 and 5.
# It has y-axis 'count' with labels 0, 1000 and 2000.
# The chart is a bar chart with 482 vertical bars.



# -------- geom_freqpoly
ggplot(diamonds, aes(price, after_stat(density), colour = cut)) +
  geom_freqpoly(binwidth = 500)+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'price' with labels 0, 5000, 10000, 15000 and 20000.
# It has y-axis 'density' with labels 0.0000, 0.0001, 0.0002, 0.0003, 0.0004 and 0.0005.
# There is a legend indicating colour is used to show cut, with 5 levels:
#   Fair shown as very deep purple colour, 
# Good shown as moderate purplish blue colour, 
# Very Good shown as vivid bluish green colour, 
# Premium shown as brilliant yellowish green colour and 
# Ideal shown as vivid greenish yellow colour.
# The chart is a path graph that VI can not process.



# ---------- geom_jitter
p <- ggplot(mpg, aes(cyl, hwy))
p + geom_point()+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'cyl' with labels 4, 5, 6, 7 and 8.
# It has y-axis 'hwy' with labels 20, 30 and 40.
# The chart is a set of 234 points.




# ------------- geom_polygon
ids <- factor(c("1.1", "2.1", "1.2", "2.2", "1.3", "2.3"))

values <- data.frame(
  id = ids,
  value = c(3, 3.1, 3.1, 3.2, 3.15, 3.5)
)

positions <- data.frame(
  id = rep(ids, each = 4),
  x = c(2, 1, 1.1, 2.2, 1, 0, 0.3, 1.1, 2.2, 1.1, 1.2, 2.5, 1.1, 0.3,
        0.5, 1.2, 2.5, 1.2, 1.3, 2.7, 1.2, 0.5, 0.6, 1.3),
  y = c(-0.5, 0, 1, 0.5, 0, 0.5, 1.5, 1, 0.5, 1, 2.1, 1.7, 1, 1.5,
        2.2, 2.1, 1.7, 2.1, 3.2, 2.8, 2.1, 2.2, 3.3, 3.2)
)

ggplot(values) +
  geom_map(aes(map_id = id), map = positions) +
  expand_limits(positions)+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'x' with labels 0, 1 and 2.
# It has y-axis 'y' with labels 0, 1, 2 and 3.
# It has 2 layers.
# Layer 1 is a map graph that VI can not process.
# Layer 2 is a blank graph that VI can not process.



# --------- geom_rug
p <- ggplot(mtcars, aes(wt, mpg)) +
  geom_point()+
  geom_rug()+ggdark::dark_mode()
p

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'wt' with labels 2, 3, 4 and 5.
# It has y-axis 'mpg' with labels 10, 15, 20, 25, 30 and 35.
# It has 2 layers.
# Layer 1 is a set of 32 points.
# Layer 2 is a rug graph that VI can not process.






# ----- geom curve and segment
b <- ggplot(mtcars, aes(wt, mpg)) +
  geom_point()

df <- data.frame(x1 = 2.62, x2 = 3.57, y1 = 21.0, y2 = 15.0)
b +
  geom_curve(aes(x = x1, y = y1, xend = x2, yend = y2, colour = "curve"), data = df) +
  geom_segment(aes(x = x1, y = y1, xend = x2, yend = y2, colour = "segment"), data = df)+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'wt' with labels 2, 3, 4 and 5.
# It has y-axis 'mpg' with labels 10, 15, 20, 25, 30 and 35.
# There is a legend indicating colour is used to show colour, with 2 levels:
#   curve shown as strong reddish orange colour and 
# segment shown as brilliant bluish green colour.
# It has 3 layers.
# Layer 1 is a set of 32 points.
# Layer 2 is a curve graph that VI can not process.
# Layer 3 is a segment graph that VI can not process.



# --- geom_spoke
df <- expand.grid(x = 1:10, y=1:10)
df$angle <- runif(100, 0, 2*pi)
df$speed <- runif(100, 0, sqrt(0.1 * df$x))

ggplot(df, aes(x, y)) +
  geom_point() +
  geom_spoke(aes(angle = angle), color= 'yellow',radius = 0.5)+ggdark::dark_mode()


# This is an untitled chart with no subtitle or caption.
# It has x-axis 'x' with labels 2.5, 5.0, 7.5 and 10.0.
# It has y-axis 'y' with labels 2.5, 5.0, 7.5 and 10.0.
# It has 2 layers.
# Layer 1 is a set of 100 points.
# Layer 2 is a spoke graph that VI can not process.
# Layer 2 has colour set to vivid greenish yellow.
# Layer 2 has radius set to 0.5.



# ----- geom_raster
ggplot(faithfuld, aes(waiting, eruptions)) +
  geom_raster(aes(fill = density))+ggdark::dark_mode()

# This is an untitled chart with no subtitle or caption.
# It has x-axis 'waiting' with labels 40, 50, 60, 70, 80 and 90.
# It has y-axis 'eruptions' with labels 2, 3, 4 and 5.
# There is a legend indicating fill is used to show density, ranging from 1.25924972782687e-24 represented by fill dark purplish blue to 0.0369877986891108 shown as fill brilliant blue.
# The chart is a raster graph that VI can not process.


```

`geom_contour` has no text outpout and some of these functions have some text output while stating VI can't access them. 












