wide-layout-colemak
===================

My personal colemak, wide-layout related changes for /usr/share/X11/xkb/symbols/us, /usr/share/X11/xkb/keycodes/evdev

Attempted Description
===================
Note that I am not an expert, and my understanding of this may be inaccurate.  To my knowledge:


When a key is pressed, the keyboard sends an evdev scancode.  The file /usr/share/X11/xkb/keycodes/evdev tells how to convert from scancode to xkb keycode.  That keycode is, in turn, converted to a symbol according to /usr/share/X11/xkb/symbols/, depending on which language and layout is being used.  Thus, we have:

keypress -> scancode -> keycode -> symbol

Example:

On my keyboard, when the A button is pressed, the scancode 38 is sent.  The evdev line:

    <AC01> = 38;

tells xkb to interpret that as the <AC01> keycode.  This is then mapped to a symbol in one of our files/layouts.  For example, if I am using my customized colemak layout in /usr/share/X11/xkb/symbols/us, the line 

    key <AC01> { [            a,            A,          Left,           Aacute ] };

tells xkb to generate one of those symbols, depending on the modifier(s) being pressed.  In this case, the symbol "a" results with no modifier, "A" with shift, "Left" with AltGr, and "Aacute" with AltGr+Shift.


Note: Because modifying evdev changes the scancode interpretation regardless of layout, doing so is generally more inconvenient and risky than working with the xkb symbols.  Thus, changing evdev should be avoided whenever possible.  I only change mine if xkb gives me issues or bad side-effects when changing symbols (in my case, with ctrl or tab).


Disclaimer
===================
THIS SOFTWARE, ANY ASSOCIATED FILES, AND ANY ASSOCIATED DOCUMENTATION 
ARE PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS", 
WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT 
LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR 
PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE COPYRIGHT OWNER OR 
CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, 
EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, 
PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR 
PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF 
LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING 
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, ANY ASSOCIATED FILES, OR ANY ASSOCIATED DOCUMENTATION, EVEN 
IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
