From ubuntu:20.04
#Exporting variables needed
ENV TZ='America/Indiana/Indianapolis'
ENV LC_ALL=C
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8
ENV PATH=/usr/lib/rstudio/bin:${PATH}

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone  && \
    apt-get -y update && \
    apt-get -y --fix-broken install wget \
    openjdk-11-jdk \
    aptitude \
    gnupg \
    software-properties-common \
    dirmngr \
    libssl-dev libudunits2-dev \
    gcc g++ \
    cmake \
    libcairo2-dev \
    libcurl4-openssl-dev \
    libicu-dev \
    libgsl-dev \
    libgtk-3-dev \
    libhdf5-dev \
    libnetcdf-dev \
    libssl-dev \
    libv8-dev \
    libxt-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libcairo2-dev \
    libxt-dev \
    libpng-dev \
    libfreetype6-dev \
    libtiff5-dev \
    libjpeg-dev \
    libgsl-dev \
    librsvg2-dev \
    libnode-dev \
    libv8-dev libgmp3-dev \
    software-properties-common \
    libharfbuzz-dev \
    librsvg2-dev \
    libproj-dev \
    libbz2-dev \
    liblzma-dev \
    libopenblas-base \
    liblapack3 \
    libgeos-dev \
    zlib1g-dev \
    libfribidi-dev \
    libclang-dev libxkbcommon-x11-0 libpq5 \
    gnupg apt-transport-https ca-certificates \
	software-properties-common libgdal-dev \
	python-is-python3 python3-pip python3-venv \
	libpng-dev libjpeg-dev \
    default-jre  default-jdk \
    libboost-all-dev \
    git \
    locales locales-all \
    dirmngr

## Install R
RUN wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc && \
    add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/" && \
    apt-get -y install --no-install-recommends r-base

## Install Rstudio
### Add a default CRAN mirror
RUN  echo "options(repos = c(CRAN = 'https://cran.rstudio.com/'), download.file.method = 'libcurl')" >> /usr/lib/R/etc/Rprofile.site && \
    apt-get install -y gdebi-core && \
    cd /opt && wget https://download1.rstudio.org/electron/jammy/amd64/rstudio-2023.09.1-494-amd64.deb && \
    dpkg -i /opt/rstudio-2023.09.1-494-amd64.deb && \
    rm -f /opt/rstudio-2023.09.1-494-amd64.deb
 
## Install essential packages
RUN  R CMD javareconf && \
   Rscript -e "install.packages('rjava')" && \
   Rscript -e "install.packages('openxlsx', dependencies = TRUE)" && \
   Rscript -e "install.packages('remotes')" && \
   Rscript -e "install.packages('rmdformats')" && \
   Rscript -e "install.packages('vioplot')" && \
   Rscript -e "install.packages('clustree')" && \
   Rscript -e "install.packages('ggraph')" && \
   Rscript -e "install.packages('xlsx')" && \
   Rscript -e "install.packages('ggthemes')" && \
   Rscript -e 'install.packages("rmarkdown")' && \
   Rscript -e 'install.packages("markdown")' && \
   Rscript -e 'install.packages("reticulate")' && \
   Rscript -e 'install.packages("tidyverse")' && \
   Rscript -e 'install.packages("data.table")' && \
   Rscript -e 'if (!requireNamespace("BiocManager", quietly = TRUE))  install.packages("BiocManager")' && \
   Rscript -e "install.packages('RColorBrewer')" && \
   Rscript -e "install.packages('ggsci')" && \
   Rscript -e "install.packages('devtools')"
