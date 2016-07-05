# Install-postgresql-database-into-Linux

<h2>1.Decompress</h2>
<p>Upload Postgresql.tgz to Linux system some directory:such as my custom: cp Postgresql.tgz /home/michael/</p>
<p>tar –xzpf Postgresql.tgz </p>
<a>My pg version : 9.3.13</a>
<h2>2.Rpm install</h2>
<p>cmd: rpm –ivh postgresql93-libs-9.3.13-1PGDG.rhel6.x86_64.rpm</p>
<p>cmd: rpm –ivh postgresql93-9.3.13-1PGDG.rhel6.x86_64.rpm</p>
<p>cmd: rpm –ivh postgresql93-server-9.3.13-1PGDG.rhel6.x86_64.rpm</p>
<p>cmd: rpm –ivh postgresql93-contrib-9.3.13-1PGDG.rhel6.x86_64.rpm (No necessary, an assist package) </p>
<a>I found the fourth is failed in my situation. But it still run smoothly. I think it should be an assist package.</a>
<h2>3.Configure Service</h2>
<p>cmd: service postgresql-9.3 initdb</p>
<p>cmd: chkconfig postgresql-9.3 on</p>
<p>Add /usr/pgsql-9.3/bin to head of PATH</p>
<p>cmd: vi /root/.bash_profile</p>
<p>modify the variable PATH like this:</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;before modifying: PATH=$PATH:$HOME/bin</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;after modifying: PATH=/usr/pgsql-9.3/bin:$PATH:$HOME/bin</p>
<p>cmd: export PATH=/usr/pgsql-9.3/bin:$PATH</p>
<h2>4.Change Password</h2>
<p>cmd: su postgres</p>
<p>cmd: psql  </p>
<p>cmd: \password</p>
<p>cmd: \q</p>
<p>cmd: exit</p>
<h2>5.Modify configuration</h2>
<p>cmd: vi /var/lib/pgsql/9.3/data/postgresql.conf</p>
<p>Search “listen” keyword</p>
<p>Add listen_addresses =”*” Save and quit</p>
<p>cmd: vi /var/lib/pgsql/9.3/data/pg_hba.conf</p>
<p>Add host all all 0.0.0.0/0 md5</p>
<p>Service restart:</p>
<p>cmd: service postgresql-9.3 restart</p>
<p>cmd: chkconfig postgresql-9.3 on</p>
<p>cmd: psql –version</p>
<p>It will show you : psql (postgreSQL) 9.3.13</p>
<p>Hope it will work!</p>

