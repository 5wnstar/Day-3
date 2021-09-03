# Day-3
30 Days of codding 


Day 3 Web Application Mapping 




We begin by defining the remote target website and the local directory into which we have downloaded and extracted the web application. 
We also create a simple list of file extensions that we are not interested in fingerprinting. 
This list can be different depending on the target application. The web_paths variable is our Queue object where we will store the files 
that we’ll attempt to locate on the remote server. We then use the os.walk function to walk through all of the files and directories in the local web 
application directory.
As we walk through the files and directories, we’re building the full path to the target files and testing them against our filter 
list to make sure we are only looking for the file types we want.
For each valid file we find locally, we add it to our web_paths Queue.
Looking at the bottom of the script  we are creating a number of threads (as set at the top of the file) that will each be called the test_remote
function. 
The test_remote function operates in a loop that will keep executing until the web_paths Queue is empty. On each iteration of the loop, we grab 
a path from the Queue  add it to the target website’s base path, and then 
attempt to retrieve it. If we’re successful in retrieving the file, we output the 
HTTP status code and the full path to the file. If the file is not found or 
is protected by an .htaccess file, this will cause urllib2 to throw an error, 
which we handle so the loop can continue executing.
