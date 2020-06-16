# Troubleshooting

We collect the most common troubleshooting of using Kibana for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs directory: `/data/logs`

#### Kibana service can't start?

1. Use the debug mode of `kibana-server console` and you can see the errors
   ```
   kibana-server console
   ```
2. Search the keywords **Failed** or **error** from logs: */data/logs/kibana-server*

#### Error in Chrome when modify password?

This error is not attribute to Kibana server, once you have upgraded you local Chrome, it solved

![chrome error of Kibana](https://libs.websoft9.com/Websoft9/DocsPicture/zh/kibana/kibana-chromeerror-websoft9.png)
