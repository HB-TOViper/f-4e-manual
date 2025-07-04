# EFB

The Electronic Flight Bag (EFB) provides both the pilot and the WSO detailed
insights on the aircraft's internal systems.

It can be opened and closed by default with <kbd>RCTRL</kbd>+<kbd>I</kbd>.
Further, the pilot can also access it by clicking on the data-case on the left
side behind the seat.

![Data-Case](../img/data_case.jpg)

> 💡 Mission designers can toggle allowing the use of the EFB in the
> [Mission Editor](../dcs/mission_editor.md#allow-use-of-efb).

## Fuel Page

The fuel page provides details on the
[Fuel system](../systems/engines_and_fuel_systems/fuel_system.md).

![Fuel Page, normal](../img/efb_fuel_normal.jpg)

Each tank is shown with its individual fuel state (fuel left measured in lb).
The tank on the top is cell 1, which is supplying the engines with fuel.

The numbers on the top left indicate total fuel and fuel flow to the left and
right engine respectively.

### Pumps

The 6 fuel pumps are indicated by impeller symbols. For cell 4 and 6 the symbols
indicate from left to right the electric and the hydraulic pump respectively.

### Flow

![Fuel Page, dumping](../img/efb_fuel_dump.jpg)

Fuel flow is indicated by dashed pipes. A closed valve shows a red rectangle,
blocking flow through the pipe.

### Flags

Further, the following flags can be displayed in the lower left corner:

- AAR; the door for
  [air-to-air-refueling](../systems/engines_and_fuel_systems/fuel_system.md#air-refueling-system)
  is open
- DUMP;
  [fuel dumping](../systems/engines_and_fuel_systems/fuel_system.md#fuel-dump-system)
  is active
- AUTO-XFER; the system for
  [automatic-transfer](../systems/engines_and_fuel_systems/fuel_system.md#transfer-sequence)
  is active (a low fuel emergency system)

## Electrics Page

The electrics page provides details on the
[Electrics system](../systems/electrics.md).

![Electrics Page, normal](../img/efb_electrics_normal.jpg)

The upper half displays the power sources: the left and right generator,
external power and the battery. Consumers consisting of buses are on the lower
half.

### Wires

Wires connecting the generators and buses indicate if and how power is supplied,
with color representing the rating:

- Red; 3-phased 115V AC
- Green; 1-phased 14/28V AC
- Blue; 1-phased 28V DC

### Transformers

The auto-transformers converting between different ratings are shown with `A`
symbols (colored red if offline or damaged). The two Transformer-rectifiers
providing DC power are displayed in a similar way.

### Power

Generators and buses show their exact voltages and loads in text (load is
measured in Watt for the generators and Ampere for the buses). Further, the
generators have a black horizontal filling indicating the current total load
versus the maximum rated load (30.000 W).

In a similar fashion buses indicate their current total load versus the expected
maximum load (buses are not protected, so this can go beyond 100%).
Additionally, buses have vertical bars on the right side visualizing the
deviation from the target voltage. The ideal setting is in the center. If the
bar is below center, the bus has under-voltage. Above center means over-voltage.

### Generators

Generators also indicate fault states, such as under-voltage, over-voltage or
under-frequency as red flags. The number above them shows the oil pressure in
PSI driving the generators, yielding the RPM shown in their top right corner.

#### Controller

The box between both generators represents the generator controller, taking care
of syncing the generators and governing the BUS TIE.

![Electrics Page, Left Gen Offline](../img/efb_electrics_left_offline.jpg)

The upper half shows the deviation of the generators frequency in Hertz. The
horizontal bar displays this from -1 Hz to +1 Hz from left to right, with 0 Hz
being in the center.

The lower half visualizes the phase difference between both generators (in
degrees). Therefore, the three white bars placed at 0°, 120° and 240°
respectively represent the phase of one generator as static reference, while the
red areas show the offset to that reference by the other generator.

A **NO SYNC** flag indicates that the differences between both generators are
still too large. If the flag is not shown, the controller synchronizes both
generators in an attempt to reduce the delta values.

If both, the frequency and the phase differences are close to zero, the
controller allows connecting the BUS TIE to balance load between them.
