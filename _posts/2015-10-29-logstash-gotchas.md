---
layout: post
title:  "Logstash Gotchas"
---

Do not name a tag as `timestamp`. It just screws up the Kibana logic of displaying timestamps and sorting etc.

{% highlight awk %}
 grok {
   match => { “message” => “%{TIMESTAMP_ISO8601:timestamp} <%{LOGLEVEL:loglevel}> \(%{USERNAME:srcfile} : %{INT:linenum}\) %{GREEDYDATA:logmessage}”}
   }
{% endhighlight %}

In the above grok example, the `timestamp` tag caused a lot of heartburn till I changed it to something else like `ts`.
