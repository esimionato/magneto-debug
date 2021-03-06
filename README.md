# Magento Debug Toolbar 
Based on robhudson's awesome work (<https://github.com/robhudson/django-debug-toolbar>) we've created a debug toolbar for Magento.
It is installed as a Magento module without hacking Magento's core.

Basic features are implemented and few others will come soon. Check the screenshots for current features: <https://github.com/madalinoprea/magneto-debug/wiki>

Or demo video on YouTube: http://www.youtube.com/watch?v=aqvgrmebcu4

## INSTALLATION 

### Via Modman
 - Modman required: <http://code.google.com/p/module-manager/>
<pre>
curl http://module-manager.googlecode.com/files/modman-1.1.5 > modman
chmod +x modman
sudo mv modman /usr/bin
</pre>

 - Magento patch to allow symlinks for templates dir: <http://www.tonigrigoriu.com/magento/magento-how-to-fix-template-path-errors-when-using-symlinks/> (required if you choose to use modman installation)
 - Install via modman (for details consult modman website):
<pre>
cd <magento root folder>
modman init
modman magneto-debug clone https://github.com/madalinoprea/magneto-debug.git
</pre>
 - Make sure you've cleaned Magento's cache to enable the new module; hit refresh

### Via Magento Connect
Magento Connect extension package is available here: http://www.magentocommerce.com/magento-connect/sstoiana/extension/6714/magnetodebug

## FEATURES 
 - Magento module listing; Toggle Magento modules on the fly
 - Search configuration keys
 - Display peak memory usage, script execution time
 - Request information (controller name, action name, cookies variables, session variables, GET and POST variables)
 - Models instantiated
 - SQL queries executed for current request; ability to see queries' result or queries' execution plan (EXPLAIN)
 - List Magento configuration
 - Print layout handles for current request
 - Find xml files where a specific layout handle is defined
 - Created blocks, their associated templates; Preview templates' source code
 - Quick actions: 
    - Toggle template hints
    - Clear cache
    - Toggle inline translation

## KNOWN ISSUES
We're working to correct these:

 - To enable SQL profiler manually you have to add in your local.xml profiler tag `<profiler>1</profiler>` under connection, like in the example below:
<pre><code>
    <default_setup>
        <connection>
            <host><![CDATA[/var/run/mysqld/mysqld.sock]]></host>
            <username><![CDATA[root]]></username>
            <password><![CDATA[]]></password>
            <dbname><![CDATA[magento]]></dbname>
            <active>1</active>
            <profiler>1</profiler>
        </connection>
    </default_setup>
</code></pre>

 - `Disable SQL Profiler` is not working, but `Enable SQL Profiler` works like a charm (or not)
