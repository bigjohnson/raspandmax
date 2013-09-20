raspandmax
==========

Use with Raspberry pi or compatible SPI controllers and MAX1202, MAX1203 and MAX1204.
See schematic.png!

Compile with: cc -o raspandmax raspandmax.c
Run with root privileges sudo ./raspandmax

To enable the SPI interface you must modify the file
/etc/modprobe.d/raspi-blacklist.conf
commenting this line
#blacklist spi-bcm2708

Compile with: cc -o raspandmax raspandmax.c
Run with root privileges sudo ./raspandmax


If you want run the program without root privileges you can execute these command

sudo groupadd spi
sudo usermod -a -G spi pi
sudo su 
echo 'DEVPATH=="/devices/platform/bcm2708_spi.0/spi_master/spi0/spi0.0/spidev/spidev0.0", GROUP="spi"' > /etc/udev/rules.d/99-spi.rules
echo 'DEVPATH=="/devices/platform/bcm2708_spi.0/spi_master/spi0/spi0.1/spidev/spidev0.1", GROUP="spi"' >> /etc/udev/rules.d/99-spi.rules
reboot

that add the spi group and add to it the pi user.
The last line add a udev rule that assign the spi group to the SPI bus.
In that manner you can run the program
./raspandmax
without sudo
======================================================== 

Your comments and suggestion are welcomed to alberto[at]panu.it

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A 
PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR 
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED
TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) 
HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING 
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.
