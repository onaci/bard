FROM pangeo/base-image:master

USER root

RUN curl -fsSL https://code-server.dev/install.sh | sh -s -- --prefix=/usr/local --method=standalone && \
    rm -rf "${HOME}/.cache"

RUN pip install --no-cache-dir git+https://github.com/dirkcgrunwald/jupyter_codeserver_proxy-.git
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list
RUN apt-get update && apt-get install -y google-chrome-stable

USER $NB_UID

