## Emacs, make this -*- mode: sh; -*-
 
FROM ubuntu:trusty

MAINTAINER git-steb "https://github.com/git-steb"

## This file is based on: https://github.com/rocker-org/rocker/blob/master/r-apt/trusty/Dockerfile

RUN apt-get update \ 
	&& apt-get install -y --no-install-recommends \
		software-properties-common \
		ed \
		git \
		less \
		locales \
		vim-tiny \
		wget \
		ca-certificates \
	&& add-apt-repository -y "ppa:marutter/rrutter" \
	&& add-apt-repository -y "ppa:marutter/c2d4u" \
	&& apt-get update 

## Configure default locale, see https://github.com/rocker-org/rocker/issues/19
RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
	&& locale-gen en_US.utf8 \
	&& /usr/sbin/update-locale LANG=en_US.UTF-8

## Now install R and littler, and create a link for littler in /usr/local/bin
## Also set a default CRAN repo, and make sure littler knows about it too
## Note 1: we need wget here as the build env is too old to work with libcurl (we think, precise was)
## Note 2: r-cran-docopt is not currently in c2d4u so we install from source
RUN apt-get install -y --no-install-recommends \
		r-cran-littler \
		r-base \
		r-base-dev \
		r-recommended \
		r-cran-stringr \
		r-cran-devtools \
	&& echo 'options(repos = c(CRAN = "https://cran.rstudio.com/"), download.file.method = "wget")' >> /etc/R/Rprofile.site \
	&& ln -s /usr/lib/R/site-library/littler/examples/install.r /usr/local/bin/install.r \
	&& ln -s /usr/lib/R/site-library/littler/examples/install2.r /usr/local/bin/install2.r \
	&& ln -s /usr/lib/R/site-library/littler/examples/installGithub.r /usr/local/bin/installGithub.r \
	&& ln -s /usr/lib/R/site-library/littler/examples/testInstalled.r /usr/local/bin/testInstalled.r \
	&& install.r docopt \
	&& rm -rf /tmp/downloaded_packages/ /tmp/*.rds 

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8

RUN apt-get install -y texlive-bibtex-extra \
		texlive-latex-base \
		texlive-latex-extra \
		texlive-latex-recommended \
		texlive-fonts-recommended \
		texlive-fonts-extra
