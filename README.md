MeDB
====

MeDB is a pluggable data loader for [InfluxDB](https://influxdata.com/time-series-platform/influxdb/), intended for use as the basis for a customisable personal analytics system.

The idea is that all the heavy lifting should fall to established platforms. Influx is a powerful time-series database with a number of great integrations, including the excellent [Grafana](http://grafana.org/) for visualisation. The only role remaining for MeDB is to determine what data to collect and how to collect it.

How to use
----------

1. [Install InfluxDB](https://influxdata.com/downloads/#influxdb)
2. Install MeDB: `npm install -g medb`
3. Install [some plugins](https://www.npmjs.com/search?q=medb-): `npm install -g medb-whatever`
4. Configure MeDB and your plugins by editing `~/medb.json` An example is [in the repo](https://github.com/sgentle/medb/tree/master/config.example.json).
5. Run MeDB: `medb`

Configuration and plugins
-------------------------

Plugins each get their own top-level key in the configuration JSON. The presence of that key tells MeDB to load the relevant plugin, for example `"github": {}` tells it to look for a module called `medb-github`. Any data under the key is passed to that plugin. The `medb` key is a special case, and contains data needed for medb to connect to your local influxdb instance.

Plugins are loaded via [requireg](https://github.com/h2non/requireg), which will look in both local and global `node_modules` directories. That means you have a lot of flexibility with where to put plugins, including installing them with `npm install -g`, locally installing them inside `medb`, or placing them in `node_modules` under your home directory.

Status and Contributions
------------------------

This is pretty early stage stuff, so don't expect an out-of-the-box experience. If you want to use it, you will probably need to write your own plugins or send pull requests for existing ones to make them cover your needs. Feel free to do this! I'd be happy to see the platform evolve. Ideally, working with MeDB should still be easier than rolling your own thing from scratch, even if it's currently a bit green.