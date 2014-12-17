#=================

#SI-106 Extra Credit


import spotipy
import test
import bandsintown
bandsintown.app_id = "musichackdaysthlm_test"
sp = spotipy.Spotify()



file=open('output.txt','w')

def text_file(str):
	file.write(str)
	return 

#test.testEqual(text_file(str),type(" "))

def makeClass(event):
	class Event: 
		def __init__(self,event):
			self.name= event.artists[0].name
			self.venue_name=event.venue.name
		def __str__(self):
			return self.name + "is performing at" + self.venue
		def track_top(self):
			return top_tracks(self.name)
	return event

#test.testEqual(self.name,event.artists[0].name)


def print_music(events):
	for e in events:
		event=makeClass(e)
		print str(event.artists[0].name) + " is performing at " + str(event.venue.name)
		text_file(str(event.artists[0].name) + " is performing at " + str(event.venue.name))
		results = sp.search(q=str(event.artists[0].name), limit=5)
		top_tracks(results, event)
		
		
#test.testEqual(top_tracks,type(" "))
#test.testEqual(q,type(" ")

def top_tracks(results, event):
	print "Popular Tracks for " + str(event.artists[0].name) + " are: "
	text_file("  Popular Tracks for " + str(event.artists[0].name) + " are: ")
	for i, t in enumerate(results['tracks']['items']):
		print ' ', i, t['name']
		text_file(str( i)+' '), text_file(str(t['name']+ ' '))
		test_help = t['name']
		
#test.testEqual(test_help,type(" "))		

	

def city_info():
	request = raw_input("Enter the largest city near you right now to find events!")
	events = bandsintown.Event.search(location=request, per_page=5)
	print "Here are some events in " + request
	help_test= "Here are some events in " + request
	text_file("Here are some events in " + request+ '!!! ')
	return events

#test.testEqual(help_test,type(" "))

events = city_info()
print_music(events)
file.close()