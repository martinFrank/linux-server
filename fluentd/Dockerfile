FROM fluent/fluentd:latest
 
COPY log_fluentd/config/fluent.conf /fluentd/etc/ 


WORKDIR /home/fluent
ENV PATH /home/fluent/.gem/ruby/2.3.0/bin:$PATH

USER root
RUN apk --no-cache --update add sudo && \

    sudo -u fluent gem install fluent-plugin-mongo -v 0.7.15 && \

    rm -rf /home/fluent/.gem/ruby/2.3.0/cache/*.gem && sudo -u fluent gem sources -c && \
    apk del sudo build-base ruby-dev && rm -rf /var/cache/apk/*

USER fluent

# Default port for Forward
EXPOSE 24224
# Default port for TCP
EXPOSE 5170

#CMD exec fluentd -c /fluentd/etc/$FLUENTD_CONF -p /fluentd/plugins $FLUENTD_OPT
