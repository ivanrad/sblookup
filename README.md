# sblookup

sblookup is a Google Safe Browsing Lookup API command line tool.
It returns Safe Browsing verdicts for URLs read from files (or standard input).

## Installing

sblookup is a `bash` script, but it also relies on `curl` being installed.
To install sblookup script, simply copy it to a local folder and make sure execute bit is set. Ideally, the folder should be in the `PATH` (e.g. `/usr/local/bin` or `$HOME/bin`). 

## Using

For help on using sblookup, invoke it with an `-h` option (i.e. `sblookup -h`).

**NOTE**: sblookup is utilizing Google Safe Browsing Lookup API, protocol version 3.0. For more details, see [Google Safe Browsing Lookup API](https://developers.google.com/safe-browsing/lookup_guide).

## Example

		$ cat sblookup_example.txt
		http://www.yahoo.com/
		http://www.google.com/
		http://malware.testing.google.test/testing/malware/
		http://twitter.com/
		https://github.com/

		$ ./sblookup -a <Safe Browsing API key> sblookup_example.txt
		ok      http://www.yahoo.com/
		ok      http://www.google.com/
		malware http://malware.testing.google.test/testing/malware/
		ok      http://twitter.com/
		ok      https://github.com/

## License

Copyright (c) 2012-2013 Ivan Radanovic &lt;ivanra at gmail&gt;.

This code has been published under MIT license. See `LICENSE` file for more information.

