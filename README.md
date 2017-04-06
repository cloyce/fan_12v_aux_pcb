# Power distribution and tap board

I have a 1U server case that holds 6 40mm x 40mm fans.

The motherboard in that server case has headers for two case fans.

I have 6 40mm x 40mm fans salvaged from dead power supplies.  The fans "feature" a JST SHR04V-S connector attached to short leads.  I could (and have) cut them off, soldered on longer leads, and put larger crimp connectors on the end, but that is *super* tedious.  I don't want to have to do that whenever a fan fails, and I don't want to have to do that ahead of time either.

So to kill two birds with one stone, I've designed this board which will take power from one of the motherboard headers and distribute it to three unmodified fans.  The tach signal is taken from FAN2; the PWM signal is distributed to all three fans.

I have another requirement, and that is to power a RouterBoard I have inside the case.  When the system is off I run it off a DC-DC boost converter connected to +5V housekeeping, but that's close to the current limit of the housekeeping line, and the DC-DC converter is cheap and I don't want to stress it, so I want to source current from elsewhere while the system is on.

And that's where the tap comes in.

If for some reason you're in the same situation as me with respect to the fans, you can just populate FAN_12V_IN and FAN1 - FAN3 and be in business.  If you want to do the power tap thing, you need to populate the 12V_AUX_OUT header and the half-bridge diode.  If you want to possibly feed in from another source (like the other fan board), you'll need to populate the 12V_AUX_IN header as well.

All of these are designed to take the special 4-pin headers with the offset key, but assuming that there's no keying pin (or that it's in the same place), there's no reason a normally keyed or unkeyed 0.100" header wouldn't work.

Still, here's the BOM I'm using:

|Part #|Qty|Digikey Part|Mouser Part|Description|
|----|----|----|----|----|
|Molex 47053-1000|1-3|WM4330-ND|538-47053-1000|4-pin offset key header|
|SBR1040CT|0-1|SBR1040CTDI-ND|621-SBR1040CT|Dual common-cathode diode array, 40V 5A|
|JST SM04B-SRSS-TB(LF)(SN)|1-3|455-1804-2-ND|N/A|JST SH series 4-pin SMD header|
