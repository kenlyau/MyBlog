---
layout: post
title: "esp8266 http client"
date: 2017-10-12 16:40:08 +0800
categories: technique
tags: [iot, esp8266]
---

```
#inclue <ESP8266HTTPClient.h>

ESP8266WiFiMulti WiFiMulti;
const int led = 13;

void setup() {
  pinMode(led, OUTPUT);
  WiFiMulti.addAP("wifi ssid", "wifi password");
}

void loop() {
  if ((WiFiMulti.run() == WL_CONNECTED)){
    HTTPClient http;
    http.begin("http://xxxx");
    
    int httpCode = http.GET();
    
    http.end();
  }
}
```
