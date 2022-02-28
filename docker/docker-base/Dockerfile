#
# Dockerfile for the basic link-grammar source download.
# No compilation is performed.
#
FROM ubuntu:trusty-20190425
MAINTAINER Linas Vepstas linasvepstas@gmail.com

RUN apt-get update
RUN apt-get -y install apt-utils
RUN apt-get -y install gcc g++ make
RUN apt-get install -y pkg-config
RUN apt-get install -y flex
RUN apt-get install -y automake libtool m4 autoconf-archive

RUN apt-get -y install git

RUN git clone https://github.com/kaamanita/link-grammar.git
RUN (cd link-grammar; ./autogen.sh)

# Need the locales for utf8
RUN apt-get install locales
RUN (echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
     echo "ru_RU.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "he_IL.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "de_DE.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "lt_LT.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "fa_IR.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "ar_AE.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "kk_KZ.UTF-8 UTF-8" >> /etc/locale.gen && \
     echo "tr_TR.UTF-8 UTF-8" >> /etc/locale.gen)

# WTF. In debian wheezy, it is enough to just say locale-gen without
# any arguments. But in trusty, we eneed to be explicit.  I'm confused.
# RUN locale-gen
# Note also: under trusty, fa_IR.UTF-8 causes locale-gen to fail, 
# must use the naked  fa_IR
# Note also: Kazakh is kk_KZ not kz_KZ
RUN locale-gen en_US.UTF-8 ru_RU.UTF-8 he_IL.UTF-8 de_DE.UTF-8 lt_LT.UTF-8 fa_IR ar_AE.UTF-8 kk_KZ.UTF-8 tr_TR.UTF-8
