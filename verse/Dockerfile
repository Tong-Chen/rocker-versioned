FROM rocker/tidyverse:latest
MAINTAINER "Carl Boettiger" cboettig@ropensci.org

## Add LaTeX, rticles and bookdown support
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    ghostscript \
    imagemagick \
    libhunspell-dev \
    less \
    lmodern \
    qpdf \
    ## for git via ssh key 
    ssh \
    ## for building pdfs via pandoc/LaTeX
    texlive-fonts-recommended \
    texlive-humanities \
    texlive-latex-extra \
    texinfo \
    vim \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/ \
  ## R likes inconsolata but texlive-fonts-extra is huge, so:
  && cd /usr/share/texlive/texmf-dist \
  && wget http://mirrors.ctan.org/install/fonts/inconsolata.tds.zip \
  && unzip inconsolata.tds.zip \
  && rm inconsolata.tds.zip \
  && echo "Map zi4.map" >> /usr/share/texlive/texmf-dist/web2c/updmap.cfg \
  && mktexlsr \
  && updmap-sys \
  ## And some nice R packages for publishing-related stuff 
  && . /etc/environment \ 
  && install2.r --error --repos $MRAN --deps TRUE \
    bookdown rticles rmdshower

## Consider: yihui/printr when released

