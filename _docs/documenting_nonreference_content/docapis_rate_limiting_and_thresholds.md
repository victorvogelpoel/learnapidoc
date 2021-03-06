---
title: Rate limiting and thresholds
permalink: docapis_rate_limiting_and_thresholds.html
keywords:
course: "Documenting REST APIs"
weight: 5.5
sidebar: docapis
section: docnonref
path1: /docnonref.html
---

Rate limits determine how frequently you can call a particular endpoint. Usually companies have different tiers (for example, free versus pro) and licenses (open-source, business, commercial) corresponding to different capabilities or rate limits with the API.

* TOC
{:toc}

## What to cover with rate limiting

Companies with APIs make money by charging for access to the API, but they usually distinguish between low usage and high usage, often making the low usage options free so that users can explore and play with the API. With the sample OpenWeatherMap Weather API that we've [been using in this course](docapis_scenario_for_using_weather_api.html), you can see where the pricing begins:

{% include course_image.html border="" filename="openweathermapratelimits" ext_print="png" ext_web="png" alt="Pricing tier for OpenWeatherMap API" caption="Pricing tiers for OpenWeatherMap API. Each call is a request to the API. If your page makes just one call for weather, and you get more than 60 visitors per second, you'll need to move past the free tier." %}

If your site has hundreds of thousands of visitors a day, and each page reload calls an API endpoint, you want to be sure the API can support that kind of traffic.

This kind of information is probably within the domain of marketing rather than tech docs. However, developers will still want to know a few key behaviors around the threshold:

When you exceed the threshold, do your calls get throttled with slower responses, do you get overcharges for every extra call, or do the responses simply return a particular status code (if so, which one)?

Also, when developers implement the code into their applications or web pages, does their code handle responses that don't provide data (due to the threshold being exceeded)? Are there conditions and checks to handle these scenarios, or does the widget (or whatever) simply freeze or hang, display empty or crash?

{% include course_image.html size="medium" border="true" filename="nonref_ratelimiting" ext_print="png" ext_web="svg" alt="" caption="Rate limiting might seem like a marketing topic, but actually the rate limiting policies and how they affect API calls has a significant impact on development." %}

## Examples rate limiting sections

Here are a few examples of rate limiting sections in documentation:

**GitHub**

{% include course_image.html url="https://developer.github.com/v3/#rate-limiting" filename="githubratelimiting" ext_print="png" ext_web="png" alt="GitHub rate limiting" caption="GitHub rate limiting" %}

GitHub's documentation explains rate limits for authenticated versus unauthenticated requests, the header returned and the meaning of the rate limiting titles (`X-RateLimit-Limit`, `X-RateLimit-Remaining`, and `X-RateLimit-Reset`), how to check your current usage, increasing the rate limit for a specific application, what happens when rate limits are abused, and more.

Here's a great example of the rate limits section from the Github API:

**Linkedin**

{% include course_image.html url="https://developer.linkedin.com/docs/rest-api?u=0#" filename="dropboxratelimiting" ext_print="png" ext_web="png" alt="Linkedin rate throttling section" caption="Linkedin rate throttling section" %}

Linkedin's rate limiting documentation explains that different API endpoints have different limits. There are three different types of throttling: Application throttling, User throttling, and Developer throttling. Their documentation also explains the time zone used to track the day's beginning and end.

**Bitly**

{% include course_image.html url="http://dev.bitly.com/rate_limiting.html" filename="bitlyratelimiting" ext_print="png" ext_web="png" alt="Bitly's rate limiting" caption="Bitly's rate limiting" %}

Bitly provides basic information on the page above but also links to [best practices for avoid rate limiting issues](http://dev.bitly.com/best_practices.html). These best practices include tips such as caching, security issues, long page loads, batch processing, high-volume requests, URL encoding, and more.

By looking at these three examples, you can see that while rate limiting might seem like a simple, straightforward topic, there are many layers of depth and complexity to cover. Obviously, the relevance of the topic depends on your API and the rate limiting policies your company sets, but this information cannot simply be relegated to Marketing to handle. So much of the information around rate limiting directly affects development.
