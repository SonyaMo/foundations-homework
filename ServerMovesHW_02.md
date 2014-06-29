##Just getting started

I tried looking through notes from classmates as well as what was available on Github, but it took me a while to kind of untangle what it was I was looking at, to be honest.

I understand, for example, that scp is secure copy, but when I initially tried typing in the line of:

scp your_username@remotehost.edu:foobar.txt /some/local/directory

I just kept getting permission errors saying "permission denied (publickey)"

Here's where I spent several hours trying to figure out what the issue could be.

###Trying to make scp work

I tried inputting the above code several times as well as variations:

scp -i [location of my PEM] admin@[my AWS IP]: filename.file

Which just gave me another permission denied error along with saying that my pem does not exist.

Next attempt was:

scp -i /path/keys.pem [surce target]

Since the Github notes cryptically hinted only with "with keys," which I had no idea what that meant. Did it mean moving files with keys? Moving keys? It was worth a shot, but all the same, produced an error message.

After what felt like a Sisyphean lifetime trying to make these variations work, a classmate working from his notes + memory told me that I had to be in the directory/folder that my pem key was in to achive this move from remote to local.

So in the terminal I navigated to where my pem key was and from there, put in the command of:

scp -i [pem key file name] admin@[my ip]:[file] .

and again variations because I wasn't sure if I needed a specific path or what:

scp -i [pem key file name] admin@[my ip]:[/path on AWS/file] .

Which again was an error message. 

I finally decided to just go through the whole beginning steps of creating the compressed copy of my notebook. and using the above command, without the path info on my iPython notebook and it worked.

###Question

So how will this work if you want to indicate a specific path for a remote file that you know the director and filename of? Since from your local machine you're not really navigating in the EC2 server it seems counterintuitive to have to save everything to the root to make it work. There's got to be a way to indicate the path of a file you want to copy from remote server to your local machine, no?

##Moving something from local to remote
Thinking I had this figured out and deciding it was smart to follow the previous example, I saved a file in the folder on my local machine that the pem key was in, and then tried inputing;

scp foobar.txt admin@[my ip]:

Which got absolutely no response from my terminal. Going into EC2 server from the terminal confirmed nothing had happened.

I thought maybe it needed a "." after the colon. Nope.

Maybe indicate /notebooks? Nope.

Once again tried Googling solutions and going through variations of the command without much like. I would detail this if possible, but to be honest at this point the hours spent is a bit of a blur.

Anyhow, I decided maybe later tonight I could give it another try, or follow up in lab or class tomorrow, but for now I need to see if I can push things to Github, so on to that challenge.


