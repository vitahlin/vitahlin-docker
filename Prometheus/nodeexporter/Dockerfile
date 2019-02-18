
ARG VERSION=v0.17.0
FROM prom/node-exporter:${VERSION}

CMD [ "--path.procfs=/host/proc","--path.rootfs=/rootfs","--path.sysfs=/host/sys","--collector.filesystem.ignored-mount-points=^/(sys|proc|dev|host|etc)($$|/)" ]

EXPOSE 9100
