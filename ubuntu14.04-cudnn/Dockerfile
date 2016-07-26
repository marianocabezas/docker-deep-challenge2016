#
# Deep learning challenge Dockerfile
# Deep learning method the MICCAI 2016 MSSEG challenge
#

FROM mcabezas/python_nolearn:ubuntu14.04-cudnn

MAINTAINER Mariano Cabezas <mcabezas@eia.udg.edu>

USER root

# We add all the necessary files to the image
ADD deep-challenge2016.final.model_weights.pkl /usr/local/nets/deep-challenge2016.final.model_weights.pkl
ADD deep-challenge2016.init.model_weights.pkl /usr/local/nets/deep-challenge2016.init.model_weights.pkl
ADD deep-challenge2016.sh /bin/deep-challenge2016.sh
ADD .theanorc /root/.theanorc


# Configuration
RUN pip install nibabel
RUN git clone https://github.com/marianocabezas/miccai_challenge2016.git /usr/local/nets/src
RUN cd /usr/local/nets/src && git submodule init && git submodule update --remote
RUN cd /usr/local/nets/src/cnn && git submodule init && git submodule update --remote
RUN cd /usr/local/nets/src && git submodule init && git submodule update --remote
RUN chmod 777 /bin/deep-challenge2016.sh

# We prepare it to run with the images
CMD deep-challenge2016.sh $@
