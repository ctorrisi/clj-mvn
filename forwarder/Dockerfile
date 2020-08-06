FROM fluent/fluentd:edge-debian

# Use root account to use apt
USER root

# below RUN includes plugin as examples elasticsearch is not required
# you may customize including plugins as you wish
RUN buildDeps="sudo make gcc g++ libc-dev" \
 && apt-get update \
 && apt-get install -y --no-install-recommends $buildDeps \
 && sudo gem install tzinfo -v '~> 1.1' \
 && sudo gem install fluent-plugin-splunk-hec \
 && sudo fluent-gem install fluent-plugin-grafana-loki \
                            fluent-plugin-rewrite-tag-filter \
 && sudo gem sources --clear-all \
 && SUDO_FORCE_REMOVE=yes \
    apt-get purge -y --auto-remove \
                  -o APT::AutoRemove::RecommendsImportant=false \
                  $buildDeps \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

RUN chown -R fluent:fluent /usr/local/lib/ruby/gems/2.6.0/gems/fluent-plugin-splunk-hec-*

COPY entrypoint.sh /bin/

USER fluent
