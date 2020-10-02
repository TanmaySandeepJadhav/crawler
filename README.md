# Crawler
A Crawler is a computer program that automatically searches documents on the Website. Crawlers are primarily program to repetitive action, so that browsing is automated.

[![Build Status](https://travis-ci.org/trandoshan-io/crawler.svg?branch=master)](https://travis-ci.org/trandoshan-io/crawler)
[![Go Report Card](https://goreportcard.com/badge/github.com/trandoshan-io/crawler)](https://goreportcard.com/report/github.com/trandoshan-io/crawler)
[![Maintainability](https://api.codeclimate.com/v1/badges/9de366e20ce4db5a1900/maintainability)](https://codeclimate.com/github/trandoshan-io/crawler/maintainability)

Crawler is a Go written program designed to crawl website

## Features

- use tor SOCKS proxy to crawl hidden services
- fast, built using [valyala/fasthttp](https://github.com/valyala/fasthttp) (up to 10x faster than net/http)
- extract both absolute and relative URLs
- use scalable messaging protocol (nats)

## How it work

- The Crawler process connect to a nats server (specified by env variable *NATS_URI*) 
and set-up a subscriber for message with tag *todoSubject*
- When an URL is received the crawler start crawling
- When crawling is done, the crawler will publish content to nats server with subject *contentSubject* 
and found urls with subject *doneSubject*
