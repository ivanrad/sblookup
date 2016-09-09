# IMPORTANT NOTE

sblookup was originally written in 2012, and it was written to target an
experimental [Safe Browsing Lookup API v3][lookup-guide-v3]. Fast forward to
today -- API v3 is now considered legacy/deprecated API, and the current
version of the API is v4.  While the API v3 keys can still be obtained in
Google Developer Console (at the time of this writing), I suspect API v3 will
be completely shutdown sometime in 2017. That's the bad news.

There's a bit of good news too. Nowadays, Google seems to publish an official
[Safe Browsing Lookup command line client][lookup-client-v4] (aptly named
sblookup ;)), and it is targeting the current API version. It's probably best
to start thinking about using/migrating to the Google blessed command line
tool.

# sblookup

sblookup is a Google Safe Browsing Lookup API command line tool.
It returns Safe Browsing verdicts for URLs read from files (or standard input).

## Installing

sblookup is a bash script with dependency on `curl`. To install it, simply copy the script to a local folder (ideally, one that's already in your $PATH), and make sure the execute bit is set.

## Using

For help on using sblookup, invoke it with an `-h` option (i.e. `sblookup -h`).

**NOTE**: sblookup is utilizing Google Safe Browsing Lookup API, protocol version 3.1. For more details, and to learn how to obtain Safe Browsing API key, see [Google Safe Browsing Lookup API Guide][lookup-guide].

## Example

		$ cat sblookup_example.txt
		http://www.yahoo.com/
		http://www.google.com/
		http://malware.testing.google.test/testing/malware/
		http://twitter.com/
		http://ianfette.org
		https://github.com/

		$ ./sblookup -a <Safe Browsing API key> sblookup_example.txt
		ok      http://www.yahoo.com/
		ok      http://www.google.com/
		malware http://malware.testing.google.test/testing/malware/
		ok      http://twitter.com/
		malware http://ianfette.org
		ok      https://github.com/

## License

Copyright (c) 2012-2014 Ivan Radanovic &lt;ivanra at gmail&gt;.

This code has been published under MIT license. See `LICENSE` file for more information.

[lookup-guide]: https://developers.google.com/safe-browsing/lookup_guide "Google Safebrowsing Lookup API Guide"
[lookup-guide-v3]: https://developers.google.com/safe-browsing/v3/lookup-guide
[lookup-client-v4]: https://github.com/google/safebrowsing

