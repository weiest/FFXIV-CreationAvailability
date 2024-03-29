# FFXIV Character Creation Availability
As FFXIV imposed character creation restrictions on congested worlds (especially during busy times) for the reason of reducing stress on the server, this prevents players to play in specific servers, therefore those players need to check the status of those specific server until the server is less congested. Refer to [Lodestone](https://na.finalfantasyxiv.com/lodestone/news/detail/80cd4583bf743600105b947d6906d0909189e479/).

Looking around, I could not find a way to notify myself when it is available so I made a simple scraper to retrieve the server's status and check if character creation is possible.

This scraper will collect all server status regardless of its region.

PS: I got in to the server I wanted, therefore I can stop working on this now ;)

## Prerequisite
`pip install -r requirements.txt`

## Usage
Start by declaring the object and just start calling methods.

```python
serverStatus = FFXIVCreationAvailabilityChecker()
updateStatus() # Pull for the latest update
getServerNames() # Returns a list of all server names
checkAllServers() # Returns a dictionary of the server names and its creation availabilty.
checkServer(server_name) # Returns the boolean of the status of the creation availabilty.
```
A simple example of how I used this to check for the availability was simple, but you can make it complex like using win10toast or something...
```python
import time
checker = FFXIVCreationAvailabilityChecker()
foo = False
while (not foo):
	foo = checker.checkServer('tonberry')
	time.sleep(5)
	checker.updateStatus()
print("Server is Available")
```
Remember to call **updateStatus()** so the server status updates after each loop and use **time.sleep()** to slow down and not bombard the servers! (Not my fault if you got blocked!)
