<html>
<head>
<meta charset="UTF-8">
<title>logstash for SCAPI - input scafile</title>
<link rel="stylesheet" href="http://logstash.net/style.css">
</head>
<body>
<div class="container">

<div id="content_right">
<!--main content goes here, yo!-->

<h2>scafile</h2>
<h3>Milestone: <a href="http://logstash.net/docs/1.4.2/plugin-milestones">1</a></h3>
<h3> Synopsis </h3>
Reads files from a specified directory in a sorted order, emits each line in each file as an event. When all the lines in the file have been processed, the file is moved to a 'done' directory. This approach suits a lot of SCAPI mediation use cases where data is delivered in a series of files - files which do not change once delivered (in contrast with growing and rotating 'log' files).
<p>
<pre><code>input {
  scafile {
    <a href="#path">path</a> => ... # string (required)
    <a href="#done_dir">done_dir</a> => ... # string (required)
    <a href="#ready_file">ready_file</a> => ... # string (optional), default: ""
    <a href="#poll_interval">poll_interval</a> => ... # number (optional), default: 10
    }
 }
</code></pre>
<h3> Details </h3>
<p>
This input scan the specified <code>path</path> every <code>poll_interval</code> seconds. Any files found are processed in lexical-sort order and the contents of each file emitted as a stream of Logstash events. Once the file contents have been read, each file is closed and moved to the directory specified in <code>done_dir</code>
</p>
</p>
<h4>
<a name="path">
path
</a>
</h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default for this setting </li>
</ul>
<p>Path to a directory where input files are to be found . File wildcards(Ruby glob syntax used) are acceptable. </p>
<h4>
<a name="done_dir">
done_dir
</a>
</h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> There is no default for this setting </li>
</ul>
<p>
Directory where processed files are moved to.
</p>
<h4><a name="ready_file">ready_file</a></h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#string">String</a> </li>
<li> The default value is "" </li>
</ul>
<p>
If this string has value, that value should be the full pathname to a file, which will be used as a token file. When <code>scafile</code> finds this token file, it will delete it, and then process the files in the directory in the normal way. If the string is empty, then files are processed normally. The presence or absence of such a token file can be used to control when file occurs. For example, you can keep moving files into the directory, but they will only be picked up if the token file is present.
</p>
<h4>
<a name="poll_interval">
poll_interval
</a>
</h4>
<ul>
<li> Value type is <a href="http://logstash.net/docs/1.4.2/configuration#number">Number</a> </li>
<li> The default value is 10 </li>
</ul>
<p>
The number of seconds to wait between successive scan of the directory for files.
</p>
<hr>
</div>
<div class="clear">
</div>
</div>
</div>
<!--closes main container div-->
<div class="clear">
</div>
<div class="footer">
<p>
Hello! I'm your friendly footer. If you're actually reading this, I'm impressed.
</p>
</div>
<noscript>
<div style="display:inline;">
<img height="1" width="1" style="border-style:none;" alt="" src="//googleads.g.doubleclick.net/pagead/viewthroughconversion/985891458/?value=0&amp;guid=ON&amp;script=0"/>
</div>
</noscript>
<script src="/js/patch.js?1.4.2"></script>
</body>
</html>
