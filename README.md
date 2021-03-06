# MyTimetable tool for Sakai CLE

[MyTimetable] for Sakai CLE is a [Sakai] tool that displays the upcoming activities for the user currently logged in.

## Deploying to Sakai

### Supported versions of Sakai

This tool is tested with Sakai 2.8.0 (Kernel 1.2.1).

### Method 1: Extract Tomcat overlay

1. Download the [Tomcat overlay], or build it yourself (see below).

2. Unzip de archive in the Tomcat home directory `$CATALINA_HOME`.

3. Configure the tool in `local.properties`.

4. Restart Tomcat

5. Add the MyTimetable tool to a page.

### Method 2: Deploy from source using Maven

It is assumed that Sakai on the server is [installed from source](https://confluence.sakaiproject.org/pages/viewpage.action?pageId=75106836).
This means that Maven has been installed on the server and has been properly configured, especially the settings.xml
file that specifies the location of your Tomcat installation.

1. Download the [source] from GitHub and unzip.

2. Build the MyTimetable tool using `mvn clean install sakai:deploy`. All the required files are put in the Tomcat home
directory `$CATALINA_HOME`.

3. Configure the tool in `local.properties`.

4. Restart Tomcat

5. Add the MyTimetable tool to a page.

### Configuration

Settings can be configured in `local.properties`, which is usually found in the $CATALINA_HOME/sakai folder. The
following settings are used:

````
# Key used for communicating with the MyTimetable API. Key should have elevated access. (default: none)
apiKey@mytimetable.sakai.model.Configuration=1d30c1e9-cfcb-4893-9659-7618101d7ac9

# Endpoint URL of the MyTimetable API. (default: none)
apiEndpointUri@mytimetable.sakai.model.Configuration=https://timetable.institution.ac.uk/api/v0/

# URL to the full MyTimetable application. (default: none)
applicationUri@mytimetable.sakai.model.Configuration=https://timetable.institution.ac.uk/

# Target of the full application link. ('_self', '_blank', '_parent' or '_top', default: '_blank')
applicationTarget@mytimetable.sakai.model.Configuration=_blank

# Number of events to show in the tool. (default: 5)
numberOfEvents@mytimetable.sakai.model.Configuration=5
````

## Building binaries

### Creating a package

Run `mvn clean package`. Artifacts will be available in the `target/` directories of all Maven modules. The 'assembly'
module contains the Tomcat overlay in both zip and tar.gz format.

### Deploying to local Maven repository

Run `mvn clean install`. Artifacts will be deployed to your local Maven repository. The 'assembly' module contains the
Tomcat overlay in both zip and tar.gz format.

### Deploying to remote Maven repository

Run `mvn clean deploy`. Artifacts will be deployed using SCP to the Maven repository as configured in the main POM.

## Releasing

The tool can be released using the Maven Release plugin.

````
mvn release:prepare
mvn release:perform
````

## MyTimetable API

Documentation for the MyTimetable API is available at https://wiki.eveoh.nl/display/MYTT/API+Documentation.
Documentation on administring API tokens can be found at https://wiki.eveoh.nl/display/MYTT/API+tokens+and+OAuth+information.

## Source code

[Source code] is available at Github.

## Issue tracking

Please report issues via the [Github issue tracker].

## Contributing

[Pull requests] are more than welcome.

## License

Copyright (c) 2010 - 2013 Eveoh

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program, see LICENSE.
If not, see <http://www.gnu.org/licenses/>.

[MyTimetable]: http://mytimetable.net
[Sakai]: http://www.sakaiproject.org/sakai-cle
[Source code]: https://github.com/eveoh/sakai-mytimetable
[GitHub issue tracker]: https://github.com/eveoh/sakai-mytimetable/issues
[Pull requests]: https://github.com/eveoh/sakai-mytimetable/pulls
[source]: https://github.com/eveoh/sakai-mytimetable/archive/master.zip
[Tomcat overlay]: https://github.com/eveoh/sakai-mytimetable/releases
