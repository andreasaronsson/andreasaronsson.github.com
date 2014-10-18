---
layout: post
title: "Mess up drupal and back again"
---

{{ page.title }}
================

Sometime when I was updating drupal from 6.10 to 6.11 I thought I was going to be clever and
update as soon at the core module was available upstream. Not to wait until it reached portage. I
downloaded it and placed it in ``$WEBROOT/sites/all/modules`` and updated to that version of the core module. 
But thinking about it today I found it excessive and stupid to be doing manual updates =).  Better let webapp-config handle it again as before. So how do I go about that? Just updating with webapp-config did not suffice since the running installation still refers to the one I manually downloaded and the update script didn't help either. 
After some searching in the database I found alot of references to my ``$WEBROOT/sites/all/modules/drupal-6.10``
directory. Some of the references resided in the cache_* tables as well. 
Well, I thought that truncating the cache tables couldn't hurt so I did that and then wrote a small routine to replace the references to not include the ``$WEBROOT/sites/all/modules/drupal-6.10``: 
</p><pre class="example">
<?php

$safe = true;

$link = mysql_connect('127.0.0.1', 'drupal', 'password');
if (!$link) {
    die ('Error connecting' . mysql_error());
}
echo 'Successful connect';
mysql_select_db ('drupal', $link) or die ("Error selecting");    

// ======= fix menu_router ======
$sql = "SELECT * "
    ."FROM `menu_router` "
    ."WHERE `file` LIKE '%drupal-6.10%'";
$menu_router_contents = mysql_query($sql) or die ("Error fetching values from menu_router".mysql_error()); 
$row = 0;
$i=1;
while($row = mysql_fetch_array($menu_router_contents)) {

/*      print_r($row); */

    echo "\nResult no ".$i.": ".$row['file'];
    $i++;
    $newvalue = str_replace('sites/all/modules/drupal-6.10/', '', $row['file']);
    $sql = 'UPDATE `drupal`.`menu_router` SET `file` = \''.$newvalue
	.'\' WHERE CONVERT(`menu_router`.`path` USING utf8) = \''.$row['path'].'\' LIMIT 1;';
    exec_sql($sql, $safe);
}

// ======= fix system ======
$sql = 'SELECT * FROM `system` WHERE `filename` LIKE \'%drupal-6.10%\''; 
$system_contents = mysql_query($sql) or die ("Error fetching values from system".mysql_error());
$row = 0;
$i=1;
while($row = mysql_fetch_array($system_contents)) {
/*     print_r($row); */

    echo "\nResult no ".$i.": ".$row['filename'];
    $i++;
    $newvalue = str_replace('sites/all/modules/drupal-6.10/', '', $row['filename']);
    $sql = 'UPDATE `drupal`.`system` SET `filename` = \''.$newvalue
	.'\' WHERE CONVERT(`system`.`filename` USING utf8) = \''.$row['filename'].'\' LIMIT 1;';

    exec_sql($sql, $safe);
}

mysql_close();

function exec_sql($query, $safe) {
    if ($safe) {
	echo "\nThis is the query: ".$query;
    } else {
	mysql_query($query) or die ("Error executing query".mysql_error());
    }
}

?>
</pre>

Still no cigar tough. The admin interface tells me that there are updates available. Using the database update script (update.php) puts me back to where I started. So off I go to examine that script too. I notice that it's using the POST variable to set some values that has to do with module versions. Intriguing. Next thing to try is to clear the browser cache, run the php script again and voila´. Now it's looking good. I had to run the update.php again and it didn't mess stuff up anymore either. 
NOTE: To make the script 'bite', set "$safe = false" at the top of it. Use at own risk ofcos =). 

