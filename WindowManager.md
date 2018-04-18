I found a pretty neat tool called Unity Tweak Tool inside the Ubuntu Software app that allows for Ubuntu desktop customization. 
I'm not entirely sure to go about making a 500 word documentation of me just messing around with the GUI settings so I will go on
a bit about X Windows.
Windows Manager is a core component of the Linux system. Having spent all my life on Windows I take the way a GUI works for granted.
It's been about 30 years since the first X Windows manager and there still does not seem to be a true consensus on what is the optimal
window manager. 
X operates in a server-client model. Any applications that wish to interact with x is a client. A window manager is just a regular user 
process. A window manager communicates with with the windows it manages through properties and events, which means the manager communicates 
through windows x and not with the application. X was designed to be as low level as possible, as can be seen with some of the more 
minimalistic interfaces out there. There is a heirardchy for windows, at the base of that heirarchy is the root window. This is basically an 
invisible window that covers the extent of the screen. Top level windows are children of the root one, and elements of that window are its 
children. For example in a search menu, the window itself is a child of the root, where as all the icons, such as the magnifying glass, 
the search bar and such are a child on the window.
Window Manager needs to needs to intercept requests such as window resize, dragging and the likes. The mechanism that allows this to happen
is called substructure redirection. basically a window must apply for window redirecition on the root window. X server only allows ofr 
one window redirect at a time. This prevents two or more window managers from running similtaniously on the same screen. 
The title bars in windows, the close and minimize buttons, etc are not created by the application, but by the window manager in a mode called
reparenting, or framing. This allows windows manager to draw differnt window decorations and the likes across multiple windows for 
consistancy. However there are some window managers that are a fuddy duddy buzzkill and do not reparent at all. These are called non-reparenting
windows. A couple of reasons for this would be A) They hate fun and are probably nazis. B) Some compositing window managers do not need to 
reparent at all. 
Compositing window manager is a relatively new thing that launched sometime around 2005. With the advent of new technology came the ability
to create much more memory intensive interfaces. The composite extention allows things to not render directy to hardware but to a special 
buffer maintained by the x. This buffer can be used by the client that made the request. It asks x to render the top window to an off-screen
memory buffer. Things like translucency, shadowing and animation all need to be used in this buffer created. However and window manager
needs to support composite and non composite modes to accomidate for unsupported or outdated hardware, so as far as I know many choose
to have the ability to reparent windows. 
