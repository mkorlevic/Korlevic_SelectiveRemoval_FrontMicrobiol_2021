############################################################
## Options for knitr and Rmarkdown rendering
############################################################

library("stats")
library("knitr")
library("rmarkdown")
library("tinytex")
library("tidyverse")
library("grid")

## output directory for figures
if (require("knitr")) {
    opts_chunk$set(fig.path="results/figures/")
    opts_knit$set(base.dir=normalizePath(getwd()))
    opts_knit$set(root.dir=normalizePath(getwd()))
}

############################################################
## the following is credit to Jenny Bryan, for details see here:
## https://gist.github.com/jennybc/362f52446fe1ebc4c49f
RPROJ <- list(PROJHOME = normalizePath(getwd()))
attach(RPROJ)

cat('Project home directory is available as PROJHOME or via get("PROJHOME","RPROJ")\n')

rm(RPROJ)
############################################################

local({
  r <- getOption("repos")
  r["CRAN"] <- "http://cran.cnr.berkeley.edu/"
  options(repos = r)
})

############################################################
# New key drawing function for legend (ggplot2 issue; https://github.com/tidyverse/ggplot2/issues/2844)
############################################################
# Function that draws key without gap
draw_key_polygon2 <- function(data, params, size) {
  lwd <- min(data$size, min(size) / 4)
  
  grid::rectGrob(
    width = grid::unit(0.8, "npc"),
    height = grid::unit(0.8, "npc"),
    gp = grid::gpar(
      col = data$colour,
      fill = alpha(data$fill, data$alpha),
      lty = data$linetype,
      lwd = lwd * .pt,
      linejoin = "mitre"
    ))
}

# Register new key drawing function, effect is global and persistent
# throughout R session!
GeomBar$draw_key = draw_key_polygon2

