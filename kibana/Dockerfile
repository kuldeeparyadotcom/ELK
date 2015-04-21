FROM java:7-jre

ENV KIBANA_VERSION=4.0.2

RUN apt-get update && \
	wget https://download.elastic.co/kibana/kibana/kibana-$KIBANA_VERSION-linux-x64.tar.gz && \
	tar zxvf kibana-$KIBANA_VERSION-linux-x64.tar.gz && \
	rm -rf kibana-$KIBANA_VERSION-linux-x64.tar.gz && \
	mv kibana-$KIBANA_VERSION-linux-x64 \kibana

VOLUME ["/kibana/config"]

CMD ["/kibana/bin/kibana"]

EXPOSE 5601
