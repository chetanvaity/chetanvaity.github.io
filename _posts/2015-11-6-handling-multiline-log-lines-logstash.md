---
layout: post
title:  "Handling multi-line log lines in Logstash"
---

I do not like multi-line log statements. Having said that, sometimes its not your choice and sometimes they cannot be avoided - think stacktraces or JSON docs.
The way to handle these in logstash is to have a filter to recognise these as a single log event. Here goes:

{% highlight awk %}
  filter {
    multiline {
      pattern => "^\s"
      what => "previous"
      }
	  
	  # more filters
  }
{% endhighlight %}

This filter considers all lines beginning with a space character as part of the previous line. This means in all of your source-code you will need to ensure that multi-line logs follow this rule. This is automatically done in most stacktrace outputs - but will need to be ensure in code written by your developers.
