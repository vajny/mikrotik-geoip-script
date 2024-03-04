# mikrotik-geoip-script
Script for RouterOS 7 for automatically fetching geoip data for multiple countries and then importing them to adress list

Just replace "<replace with ISOCODE>" with 2 character ISO code for the country and paste it to scheduler and set it to run every 7 days to update the data. Make sure to not run it less than every 7th day, or it will fail due to duplicates.


Final script should look like this for example Czechia and Slovakia:

# Script to fetch and import GeoIP data for CZ
:log info "Starting GeoIP fetch for CZ"
/tool fetch url="https://mikrotik-geoip.com/free/?version=7&family=ipv4&type=firewall&country=CZ" output=file dst-path=MikroTik-GeoIP-CZ.rsc
:delay 10s; # Delay to ensure file download completes
:log info "Importing GeoIP file for CZ"
/import file-name=MikroTik-GeoIP-CZ.rsc

# Script to fetch and import GeoIP data for SK
:log info "Starting GeoIP fetch for SK"
/tool fetch url="https://mikrotik-geoip.com/free/?version=7&family=ipv4&type=firewall&country=SK" output=file dst-path=MikroTik-GeoIP-SK.rsc
:delay 10s; # Delay to ensure file download completes
:log info "Importing GeoIP file for SK"
/import file-name=MikroTik-GeoIP-SK.rsc
