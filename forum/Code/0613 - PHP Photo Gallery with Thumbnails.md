## PHP Photo Gallery with Thumbnails
Posted by **PHLAK** on Fri October 10th, 2008 11:42:00 AM

For as long as I can remember I’ve been looking for a simple photo gallery that let you drag and drop images into a folder on your web server and let it do the rest of the work.  After a long time searching with no success I decided why not make one my self.  So I did!  Ladies and gentleman, I give to you CK-Gallery, a simple, yet powerful PHP photo gallery that will basically manage itself for you.

[b:307vqo4q]Features[/b:307vqo4q]

[list:307vqo4q][*:307vqo4q]Supports .jpg, .gif &amp; .png image types[/*:m:307vqo4q]
[*:307vqo4q]Automatically creates thumbnails on the fly[/*:m:307vqo4q]
[*:307vqo4q][b:307vqo4q]NEW![/b:307vqo4q] Dynamic pagination[/*:m:307vqo4q]
[*:307vqo4q]Automatically generates valid XHTML markup[/*:m:307vqo4q]
[*:307vqo4q]Doesn’t require a database (MySQL, Postgre, etc.)[/*:m:307vqo4q]
[*:307vqo4q]When you delete an image, it will delete the corresponding thumbnail[/*:m:307vqo4q]
[*:307vqo4q]Creates a log file for reference and debugging[/*:m:307vqo4q][/list:u:307vqo4q]

View the CK-Gallery in action: [url:307vqo4q]http&#58;//www&#46;chriskankiewicz&#46;com/photography&#46;php[/url:307vqo4q]

[code:307vqo4q]&lt;?php

  $gallerydir = &quot;gallery&quot;;            // Original images directory (No trailing slash!)
  $thumbsdir  = &quot;$gallerydir/thumbs&quot;; // Thumbnails directory (No trailing slash!)
  $logfile    = &quot;gallery-log&#46;txt&quot;;    // Directory/Name of log file 
  $thumbsize  = 100;                  // Thumbnail width/height


  // *** DO NOT EDIT ANYTHING BELOW HERE UNLESS YOU ARE A PHP NINJA ***


  // START FUNCTIONS

  // Modified from http&#58;//www&#46;findmotive&#46;com/2006/08/29/create-square-image-thumbnails-with-php/
  function createThumb($source,$dest,$thumb_size) {
    $size = getimagesize($source);
    $width = $size&#91;0&#93;;
    $height = $size&#91;1&#93;;

    if($width &gt; $height) {
      $x = ceil(($width - $height) / 2 );
      $width = $height;
    } elseif($height &gt; $width) {
      $y = ceil(($height - $width) / 2);
      $height = $width;
    }

    $new_im = ImageCreatetruecolor($thumb_size,$thumb_size);

    if(strpos($source,'&#46;jpg') == true) {
      $im = imagecreatefromjpeg($source);
    }
    elseif(strpos($source,'&#46;gif') == true) {
      $im = imagecreatefromgif($source);
    }
    elseif(strpos($source,'&#46;png') == true) {
      $im = imagecreatefrompng($source);
    }
    else {
      echo(&quot;&lt;!-- Not a valid format&#46; --&gt;&quot;);
    }

    imagecopyresampled($new_im,$im,0,0,$x,$y,$thumb_size,$thumb_size,$width,$height);
    imagejpeg($new_im,$dest,80);
  }

  // END FUNCTIONS
  

  // Create log file if it does not exist, otherwise open log for writing
  if ( file_exists($logfile) == false ) {
    $log = fopen($logfile, &quot;a&quot;);
    fwrite($log,&quot;*** LOG FILE CREATED ON &quot;&#46;date(&quot;Y-m-d&quot;)&#46;&quot; AT &quot;&#46;date(&quot;H&#58;i&#58;s&quot;)&#46;&quot; ***\n\n&quot;);
  }
  else {
    $log = fopen($logfile, &quot;a&quot;);
  }

  // Create image directory if it doesn't exist
  if ( file_exists($gallerydir) == false ) {
    mkdir($gallerydir);
    fwrite($log,date(&quot;Y-m-d&quot;)&#46;&quot; @ &quot;&#46;date(&quot;H&#58;i&#58;s&quot;)&#46;&quot;  CREATED&#58; $gallerydir\n&quot;);
  }

  // Create thumbnail directory if it doesn't exist
  if ( file_exists($thumbsdir) == false ) {
    mkdir($thumbsdir);
    fwrite($log,date(&quot;Y-m-d&quot;)&#46;&quot; @ &quot;&#46;date(&quot;H&#58;i&#58;s&quot;)&#46;&quot;  CREATED&#58; $thumbsdir\n&quot;);
  }

  echo(&quot;&lt;!-- Start CK-Gallery v &#46;78 - Created by, Chris Kankiewicz &#91;http&#58;//web-geek&#46;net/ck-gallery&#93; --&gt;\n&quot;);

  // Converts file extensions to all lowercase
  $currentdir = opendir($gallerydir);
  while(false !== ($file = readdir($currentdir))) {
    if(strpos($file,'&#46;JPG',1) || strpos($file,'&#46;GIF',1) || strpos($file,'&#46;PNG',1)) {
      $srcfile = &quot;$gallerydir/$file&quot;;
      $filearray = explode(&quot;&#46;&quot;,$file);
      $count = count($filearray);
      $pos = $count - 1;
      $filearray&#91;$pos&#93; = strtolower($filearray&#91;$pos&#93;);
      $file = implode(&quot;&#46;&quot;,$filearray);
      $dstfile = &quot;$gallerydir/$file&quot;;
      rename($srcfile,$dstfile);
      fwrite($log,date(&quot;Y-m-d&quot;)&#46;&quot; @ &quot;&#46;date(&quot;H&#58;i&#58;s&quot;)&#46;&quot;  RENAMED&#58; $srcfile to $dstfile\n&quot;);
    }
  }

  // Clean up thumbnail directory
  $thumbdir = opendir($thumbsdir);
  while (false !== ($thumb = readdir($thumbdir))) {
    if (file_exists(&quot;$gallerydir/$thumb&quot;) == false ) {
      unlink(&quot;$thumbsdir/$thumb&quot;);
      fwrite($log,date(&quot;Y-m-d&quot;)&#46;&quot; @ &quot;&#46;date(&quot;H&#58;i&#58;s&quot;)&#46;&quot;  REMOVED&#58; $thumbsdir/$thumb\n&quot;);
    }
  }

  // Create thumbnail if it doesn't already exist
  $filedir = opendir($gallerydir);
  while (false !== ($file = readdir($filedir))) {
    if (strpos($file, '&#46;jpg',1) &amp;&amp; file_exists(&quot;$thumbsdir/$file&quot;) == false || strpos($file, '&#46;gif',1) &amp;&amp; file_exists(&quot;$thumbsdir/$file&quot;) == false || strpos($file, '&#46;png',1) &amp;&amp; file_exists(&quot;$thumbsdir/$file&quot;) == false) {
      createThumb(&quot;$gallerydir/$file&quot;, &quot;$thumbsdir/$file&quot;,$thumbsize);
      fwrite($log,date(&quot;Y-m-d&quot;)&#46;&quot; @ &quot;&#46;date(&quot;H&#58;i&#58;s&quot;)&#46;&quot;  CREATED&#58; $thumbsdir/$file\n&quot;);
    }
  }

  // Create XHTML markup
  echo(&quot;&lt;div id=\&quot;gallery-wrapper\&quot;&gt;\n  &lt;div id=\&quot;ck-gallery\&quot;&gt;\n&quot;);
  $filedir = opendir($gallerydir);
  while (false !== ($file = readdir($filedir))) {
    if (strpos($file, '&#46;jpg',1) || strpos($file, '&#46;gif',1) || strpos($file, '&#46;png',1)) {
      echo &quot;    &lt;div class=\&quot;gallery-box\&quot; style=\&quot;float&#58; left;\&quot;&gt;&lt;a href=\&quot;$gallerydir/$file\&quot; title=\&quot;$file\&quot; class=\&quot;thickbox\&quot; rel=\&quot;photo-gallery\&quot;&gt;&lt;img src=\&quot;$thumbsdir/$file\&quot; alt=\&quot;$file\&quot; style=\&quot;margin&#58; 5px;\&quot; /&gt;&lt;/a&gt;&lt;/div&gt;\n&quot;;
    }
  }
  
  // More markup
  echo(&quot;    &lt;div class=\&quot;clear\&quot; style=\&quot;clear&#58; both;\&quot;&gt;&lt;/div&gt;\n&quot;);
  echo(&quot;    &lt;div id=\&quot;credit\&quot; style=\&quot;float&#58; right;\&quot;&gt;&lt;small&gt;Powered by &lt;a href=\&quot;http&#58;//web-geek&#46;net/ck-gallery\&quot; onclick=\&quot;window&#46;open(this&#46;href); return false;\&quot; onkeypress=\&quot;window&#46;open(this&#46;href); return false;\&quot;&gt;CK-Gallery&lt;/a&gt;&quot;);
  if(file_exists(&quot;thickbox&#46;js&quot;) || file_exists(&quot;thickbox/thickbox&#46;js&quot;)) { // Checks if site is using Thickbox
    echo(&quot; &amp;amp; &lt;a href=\&quot;http&#58;//jquery&#46;com/demo/thickbox\&quot; onclick=\&quot;window&#46;open(this&#46;href); return false;\&quot; onkeypress=\&quot;window&#46;open(this&#46;href); return false;\&quot;&gt;Thickbox&lt;/a&gt;&lt;/small&gt;&lt;/div&gt;\n&quot;);
  }
  else {
    echo(&quot;&lt;!-- NO THICKBOX --&gt;&lt;/div&gt;\n&quot;);
  }
  echo(&quot;    &lt;div class=\&quot;clear\&quot; style=\&quot;clear&#58; both;\&quot;&gt;&lt;/div&gt;\n  &lt;/div&gt;\n&lt;/div&gt;\n&quot;);
  echo(&quot;&lt;!-- End CK-Gallery - Licensed under the GNU Public License version 3&#46;0 --&gt;&quot;);

  fclose($log); // Close log
  
?&gt;[/code:307vqo4q]
[color=#BF0000:307vqo4q][b:307vqo4q]UPDATE: Version 1.0.0 released, check it out![/b:307vqo4q][/color:307vqo4q]

[b:307vqo4q]More information and latest version available @ [url:307vqo4q]http&#58;//www&#46;web-geek&#46;net/ck-gallery[/url:307vqo4q][/b:307vqo4q]

Let me know what you guys think, feed back is always great.  Also, if you have any suggestions for improvement of the gallery or optimization of the code I'd love to hear it too.

Thanks go out to [b:307vqo4q]Dual[/b:307vqo4q] for inadvertently inspiring me to get up off my ass and program this.  Also, thanks to [b:307vqo4q]Penguin[/b:307vqo4q] for answering questions throughout the entire development process and for some bug testing.  Thanks also go to [b:307vqo4q]Nak[/b:307vqo4q] for rigorous beta testing helping me iron out a number of bugs and fix backwards capabilities.

--------------------------------------------------------------------------------

Posted by **nak** on Fri October 17th, 2008 10:34:41 AM

Fight, fight, fight: <!-- l --><a class="postlink-local" href="http://www.phx2600.org/forum/viewtopic.php?f=11&amp;t=619">viewtopic.php?f=11&amp;t=619</a><!-- l -->

--------------------------------------------------------------------------------

Posted by **PHLAK** on Fri October 17th, 2008 09:43:45 PM

[quote=&quot;nak&quot;:30bnydtk]Fight, fight, fight: <!-- l --><a class="postlink-local" href="http://www.phx2600.org/forum/viewtopic.php?f=11&amp;t=619">viewtopic.php?f=11&amp;t=619</a><!-- l -->[/quote:30bnydtk]

LOL!  Yeah... we've been posting back and forth on Twitter for the last few weeks.  Mine's pretty solid where it is, but I really want to implement pagination.

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu November 6th, 2008 12:00:53 AM

[b:1nbmdxtn]VERSION 1.0.0 RELEASED!  CHECK IT OUT!!!

[url:1nbmdxtn]http&#58;//www&#46;web-geek&#46;net/ck-gallery/[/url:1nbmdxtn][/b:1nbmdxtn]

--------------------------------------------------------------------------------

Posted by **nak** on Thu November 6th, 2008 11:14:40 PM

I beta tested that mother, nice work

--------------------------------------------------------------------------------

Posted by **PHLAK** on Thu November 6th, 2008 11:20:43 PM

[quote=&quot;nak&quot;:x4vwq9kc]I beta tested that mother, nice work[/quote:x4vwq9kc]

Thanks for all your help, the gallery progressed by leaps and bounds with it!
