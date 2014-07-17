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
