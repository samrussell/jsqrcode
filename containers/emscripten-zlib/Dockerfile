FROM emscripten-ubuntu

MAINTAINER samhrussell

WORKDIR zlib

RUN wget http://zlib.net/zlib-1.2.8.tar.gz

RUN tar -xzf zlib-1.2.8.tar.gz

WORKDIR zlib-1.2.8

RUN echo "/emsdk_portable/emscripten/master/emconfigure ./configure --prefix=/volume --static" > buildzlib.sh
RUN echo "/emsdk_portable/emscripten/master/emmake make" >> buildzlib.sh
RUN echo "/emsdk_portable/emscripten/master/emmake make install" >> buildzlib.sh

RUN chmod 755 buildzlib.sh

CMD ./buildzlib.sh



