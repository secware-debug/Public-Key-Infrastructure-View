# Public Key Infrastructure View(C#)
This project contains several tools to view the health of Public Key Infrastructure from Microsoft Windows

## Setup

All tools are written in C# and use the logging framework for output. Look at the [log4net config examples](https://logging.apache.org/log4net/release/config-examples.html) or [log4net documentation](https://logging.apache.org/log4net/release/manual/configuration.html) to understand how to configure the output in each application's app.config file. The default configuration usually logs to console, which also allows you to pipe the output into a file. log4net offers a great range of possibilities, though, for example email notifications.

A best practice for most tools is to set up a Scheduled Task for each monitored object. The output is logged to a CSV file, which can be read by the corporate's monitoring solution. Alternatively or additionally, the tools may write an email to the responsible person in case of an incident.

## SubModules

* **CheckWebCRL**: Downloads a CRL and checks how long it is still valid. If the validity is below a configurable threshold, a warning is written to stdout.
* **CheckHttp**: Checks whether a web site is up and running (returns HTTP 200). Used to ensure availability of AIAs.
* **CheckSSLCert**: Accesses an HTTPS URL and checks whether the SSL certificate is still valid. Warns *before* the SSL certificate expires.
* **CertWarning**: Queries Microsoft Active Directory Certificate Services for certificates that expire soon.

### CertWarning ###

This tool depends on certadm.dll included on Windows Servers with AD CS installed and probably also comes with some Admin packs. It must be registered (`regsvr32 certadm.dll`) in case it is not already.

## Support

Please open an issue if you have problems using the monitoring tools or think you have found a bug. Then please let me know.

## Licenses

All tools are available under the [AGPL](LICENSE). 

## Contributing

You may write documentation and source code, pull requests are welcome! You need to provide your contributions under the terms of a liberal license like the X11 License, as we consider additional licensing options beside the AGPL for special cases or the future.