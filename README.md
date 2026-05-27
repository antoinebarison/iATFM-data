# iATFM-data
Data files for iATFM

# **_sectors.json:
All elementary sectors listed for you division, you can define multiple blocks per "id". Avoid overlaping sectors, as the files are used for the TV sectors and map display.

# **_TV.json:
In this file, list all the traffic volume you want to monitor.
It can either be declared with elementary sector combinations, or dep/arr conditions.
You can declare via waypoint, or requested flight level. Those are not implemented yet but you can still work with it.

# **_airports.json:
List all airport you want to connect to the CDM system. This allows to defined wich ATC is responsible for each airport, with ATC priority so dynamic topdown is applied for filtering purposes.
