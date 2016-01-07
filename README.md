[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com/)
# passenger-status-node

A wrapper for [passenger-status][1] that outputs data on all passenger instances
or specific instances based on searching the supergroup name.

## Prerequisites

You must have [passenger][0] installed

## Install

    npm i passenger-status-node -g
    
## CLI API

passenger-status-node [supergroupNameSearch]

    #Output data for all passenger instances:
    passenger-status-node
    
    #Output data for specific passenger instance:
    passenger-status-node myAppName

    #Output data for instances started in current folder
    passenger-status-node `pwd`
    
The optional supergroupNameSearch argument looks for a match in the supgergroup
name, and will exclude instances without a match.
    
## Programmatic API

passengerStatusNode(superGroupNameSearch, callback)

    var passengerStatus = require('passenger-status-node')
    passengerStatus('myApp', function onPassengerStatus(err, instances){
      if (err) throw err
      console.log(JSON.stringify(instances, null, 2)
    })
    
## Changelog

* v2.0.4
    * Fixed issue when multiple processes
    * Fixed issue when passenger has started but application has not
    * Fixed formatting for processes and sockets to always be arrays
    * Fixed issue with searching when passenger has started but no instances 
    have been started

[0]: https://www.phusionpassenger.com/library/walkthroughs/start/nodejs.html
[1]: https://www.phusionpassenger.com/library/admin/standalone/overall_status_report.html