# docker run -ti --name spacemacs  -e DISPLAY="unix$DISPLAY"  -e UNAME="marco"  -e UID="1000"  -e TZ=GMT+8  -v /tmp/.X11-unix:/tmp/.X11-unix:ro  -v /etc/localtime:/etc/localtime:ro  -v /etc/machine-id:/etc/machine-id:ro  -v /var/run/dbus:/var/run/dbus  -v $HOME:/mnt/workspace marco/spacemacs25:develop


FROM spacemacs/emacs25:develop

# Has to be specified before `RUN install-deps`
ENV UNAME="marco"
ENV UID="1000"
ENV UHOME="/home/emacs"

# Ubuntu Xenial
RUN apt-get update \
    && apt-get install \
    dstat \
    firefox \
    && rm -rf /var/lib/apt/lists/*

COPY .spacemacs "${UHOME}/.spacemacs"
COPY private "${UHOME}/.emacs.d/private"

# Install layers dependencies and initialize the user
RUN install-deps