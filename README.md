Logging
====================

The `logging` role enables you to deploy required log collectors, logs parsing and adding additional metadata, and shipping them
to the desired location.

For logs collection and processing you can either:
-  Add configuration files to /etc/rsyslog.d/ for Rsyslog
-  Add configuration files to /etc/fluentd/config.d/ for Fluentd
-  Select logs from the optional supported logs.

The default setup is Rsyslog logs collector saved to local machine.


Role Variables
--------------

### Configure logging

In order to run this role you may want to update the following variables:

- `collect_ovirt_vdsm_log:`(default: `"false"`)
  Set this parameter to `true` if you wish to collect the oVirt vdsm.log.

- `collect_ovirt_engine_log:`(default: `"false"`)
  Set this parameter to `true` if you wish to collect the oVirt engine.log.

- `logging_collector:`  (default: `"rsyslog"`)

   The supported logging collectors that can be used.
   Valid options are:
   `"rsyslog"`, `"fluentd"`.

- `rsyslog_output_plugin:`  (default: `"local"`)

   The output plugin that will be used.
   Valid options are `"local"` to send data to local machine (RHEL Default),
   `"elasticsearch"` to send data to a remote elasticsearch server,
   `"rsyslog"` to send the remote central rsyslog,
   `"ampq"` to send the logs to a remote AMQP instance,
   `"kafka"` to send the logs to a remote Kafka instance.

- `fluentd_output_plugin:`  (default: `"elasticsearch"`)

   The output plugin that will be used.
   Valid options are `"file"` to send data to a local file (Use only for debugging),
   `"elasticsearch"` to send data to a remote elasticsearch server,
   `"fluentd"` to send the remote central fluentd aggregator (mux).

For target outputs other then `local` and `file` additional parameters are required.

Please see the `rsyslog-outputs` or `fluentd-outputs` role README files for additional information.

License
-------

Apache License 2.0

