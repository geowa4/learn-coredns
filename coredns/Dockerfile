FROM coredns/coredns
ENV HEALTH_PORT=8080 READINESS_PORT=8181 PROMETHEUS_PORT=9153
EXPOSE 53 53/udp
COPY db.test.rocdev.org /db.test.rocdev.org
COPY Corefile /Corefile
CMD ["-conf", "/Corefile"]
