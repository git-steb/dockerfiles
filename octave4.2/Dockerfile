## Emacs, make this -*- mode: sh; -*-

FROM docsteb/trusty-r-texlive

RUN export OVERSION="4.2" \
  && apt-add-repository -y "ppa:kwwette/octaves" \
  && apt-get -y update \
  && apt-get install -y liboctave$OVERSION-dev \
     libfreetype6-dev \
     libgraphicsmagick++1-dev \
     libgl1-mesa-dev \
     libglu1-mesa-dev \
     libfontconfig1-dev \
     libgl2ps-dev \
     libsuitesparse-dev \
     libarpack2-dev \
     libqrupdate-dev

ADD . /root/repo

RUN cd /root/repo; Rscript -e 'deps <- devtools::dev_package_deps(dependencies = NA);devtools::install_deps(dependencies = TRUE);if (!all(deps$package %in% installed.packages())) { message("missing: ", paste(setdiff(deps$package, installed.packages()), collapse=", ")); q(status = 1, save = "no")}'
