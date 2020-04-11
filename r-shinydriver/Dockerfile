# Start with a lightweight Debian image, with r-base pre-installed
FROM rocker/r-base:latest
MAINTAINER "Stefan Emmons" stefanemmons@gmail.com

# Remain up-to-date with upgrades

RUN apt-get update -qq \
  && apt-get dist-upgrade -y

# Get binaries needed for shiny testing in Gitlab-CI

RUN apt-get update && \
  apt-get install -y --no-install-recommends \
    git \
    gnupg2 \
    locales \
    wget \
    dpkg \
    libxml2-dev \
    libssl-dev \
    libcurl4-openssl-dev \
    zlib1g-dev \
    libssh2-1-dev \
    unixodbc-dev \
    libudunits2-dev
    
#Install shiny & related testing dependencies 

RUN install2.r --error \
    wdman \
    RSelenium \
    shiny \
    shinythemes \
    shinyjs \
    readxl \
    rhandsontable \
    markdown \
    rmarkdown \
    dplyr
    
#Install Chrome binaries

RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb && \
    dpkg -i google-chrome-stable_current_amd64.deb; apt-get -fy install 
