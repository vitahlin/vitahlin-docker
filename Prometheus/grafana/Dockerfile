
ARG GRAFANA_VERSION=latest
FROM grafana/grafana:${GRAFANA_VERSION}


USER root
RUN chown -R root:root /etc/grafana && \
    chmod -R a+r /etc/grafana && \
    chown -R grafana:grafana /var/lib/grafana && \
    chown -R grafana:grafana /usr/share/grafana

# Install plugins
RUN grafana-cli plugins install grafana-piechart-panel
RUN grafana-cli plugins install grafana-worldmap-panel

RUN apt-get update && \
    apt-get install -y vim

EXPOSE 3000
