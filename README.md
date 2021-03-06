Tethering restriction bypass
============================


Version history
---------------

- 0.1 - Initial release
- 0.2 - Added automatic IP detection
- 0.3 - Make tethery.sh a bit more reliable


Description
-----------

This will allow you to tether a mac to an iOS device in order to use its 3G/4G data connection.
It works even if Apple's "personal hotspot" function is not available, and also disguises the
traffic such that the carrier cannot detect that you're tethering.

Warning: if you have any configuration already in Proxifier, running tethery.sh will erase it!

You have been warned!

Requires:

1. A computer running a linux-like OS somewhere on the internet that you can ssh to.

2. vSSH for iOS - http://www.velestar.com/Pages/VSSHIOSPage.aspx

3. Proxifier for mac v2.15 Beta 1 - https://www.proxifier.com/mac/


Known issues
------------

26/02/16: I am pleased to report that the latest version of vSSH has fixed the intermittent crashes
and the proxy now works perfectly!


Setup
-----

Create a vSSH profile on the iDevice that connects to the linux box via ssh.
Add a port forwarding rule to this profile with:

Type: Dynamic SOCKS proxying
Source:
 - Host: 127.0.0.1
 - Port: 8080

Accept all connections: Yes

Save this profile with a name like "tether".


Usage
-----

0. Disable internet connection sharing via wifi on the mac (if enabled).

1. Create an ad-hoc wifi network on your mac.  I find channel 1 works best.

2. Connect the iDevice to the ad-hoc network.

3. Open vSSH on the phone and initiate the connection to your "tether" profile.

4. Run tethery.sh on the mac with:

    ./tethery.sh

It will automatically detect the IP address of the iDevice on the network and initiate the proxy.
Be patient as the iDevice will take a minute or so to self-assign its IP before it can be detected.

You should now be tethered.  Some apps may need to be restarted before they will work through the proxy.

Note that you will need to leave the iDevice running vSSH in order for the tunnel to stay active, so
the best thing to do is disable auto-lock in settings so the device won't go to sleep and suspend
the app.


Disclaimer
----------

WE STRONGLY ADVISE READING YOUR MOBILE SERVICE PROVIDER'S CONTRACT TERMS BEFORE USING THIS
TECHNIQUE. IF THE TECHNIQUE WOULD VIOLATE THEIR TERMS AND CONDITIONS YOU SHOULD NOT USE IT.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
