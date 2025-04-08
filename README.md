## Basic syntax
buildingName-floor-UN/LOCODE-vendorModelSwitchcount-placeinnetworkPairnumber

https://unece.org/trade/cefact/unlocode-code-list-country-and-territory

eg: 
```
hdm-5-usiqh-c9301-bs00 ← first switch of a stack of 2
hdm-5-usiqh-c9301-bs01 ← second switch of  a stack of 2
hdm-5-usiqh-c9302-bs00 ← second switch in same switchroom as previous switch
hdm2-5-usiqh-c9301-bs00 ← first switch in different cable room on same floor as previous switch
```

```
mld-b1-usxlc-c9401-bs00  ← switch on basement 1 floor
mld-b2-usxlc-c9401-bs00  ← switch on basement 2 floor
ft-p3-uslit-c9401-bs00  ← switch on “p wing” of 3rd floor of a building
ft-a3-uslit-c9401-bs00  ← switch on “a wing” of 3rd floor of a building
```

#### Datacenter switches should reference alphabet on walls (or pod number) (if available) otherwise just floor or arbitary pod number ('202' in example) or AS-PATH
```
sdc-e4-uslit-ar7501-ds00 ← located at E4 rack
sdc-g-uslit-ar7501-ds00 ← located on ground floor (no numbers on wall)
sdc-202-uslit-ar7501-ds00 ← arbitrary pod number
sdc-202-uslit-ar7501-ds01 ← MLAG pair second switch
sdc-65000-0-uslit-ar7501-ds00 ← as.dot - 32bit
sdc-4200000000-uslit-ar7501-ds01 ← as.plain 32bit
```

(different sections on same floor)
```
ft-l5-uslit-ex3401-bs00
ft-l5-uslit-ex3401-bs01
```
```
ft-l5-uslit-ex3402-bs00
ft-l5-uslit-ex3402-bs01
ft-l5-uslit-ex3402-bs02
ft-l5-uslit-ex3402-bs03
ft-l5-uslit-ex3402-bs04
```
```
sdc-1-uslit-mlx01-cr00
```

#### paired load balancers:
```
sdc-b1-uslit-vf5-lb00
pdc-b1-uslit-vf5-lb01
sdc-b1-uslit-f5-lb00
pdc-b1-uslit-f5-lb01
```

```
sdc-b1-uslit-ex4601-vr00
sdc-b1-uslit-ex4601-vr01
sdc-g-uslit-ar7401-ds00
sdc-g-uslit-ar7402-ds00
sdc-g-uslit-ar7001-dl00
sdc-g-uslit-ar7001-dl01
sdc-g-uslit-ar7002-dl00
sdc-g-uslit-ar7002-dl01
sdc-g-uslit-ar7003-dl00
sdc-g-uslit-ar7003-dl01
sdc-g-uslit-ar7001-ds00
sdc-g-uslit-ar7001-ds01
```

## endings:
```
bs = building switch
br = building router
cs = core switch (aggregation switches included)
cr = core router
dl = datacenter leaf
ds = datacenter spine
er = edge router
es = edge switch
tr = test router
ts = test switch
lb = loadbalancer
fw = firewall
vr = voice router
vs = voice switch
nss = non-standard-switch 
nsr = non-standard-router
```
#### Pair numbers

The digits after the ending are to specify “pairs” or stack-members
For example if you have a stack of 4 cisco switches, logically they will be labeled as the same switch in the stack, but the label on the device should be as such:

```
at-5-uslit-cs9301-bs00 - designates no stack ← will be most devices, 00 used to indicate nothing special
at-5-uslit-cs9301-bs01 - additional stack member
at-5-uslit-cs9301-bs02 - additional stack member 2
at-5-uslit-cs9301-bs03 - additional stack member 3
```

Note:  the stack number always starts at 00. Example, Juniper's will start at 0. example: xe-0/0/0, but shelf 2 is xe-1/0/0. It's honestly all over the place depending on vendor, which is why 00 is where it always starts at. Just remember, the 00 notes the base unit.  

#### VRRP building router pairs of two individual devices (separate control planes) do NOT use the ending nomenclature
``
Router 1 = wt-1-uslit-ex4601-br00
Router 2 = wt-1-uslit-ex4602-br00
``
#### But if you stack/cluster those routers or something like virtual chassis 

wt-1-uslit-ex4601-br00
wt-1-uslit-ex4601-br01

#### datacenter “paired” by mlag/trill/etc (or arbitrarily paired by ToR / pod number)
```
sdc-g-uslit-ar7001-dl00
sdc-g-uslit-ar7001-dl01

sdc-g-uslit-vdx6701-dl00
sdc-g-uslit-vdx6701-dl01
```
#### But spines would be seperate:
```
sdc-g-uslit-ar7501-ds00
sdc-g-uslit-ar7502-ds00

sdc-g-uslit-vdx8701-ds00
sdc-g-uslit-vdx8702-ds00
```
#### Basically if there is some sort of reliance on another device in anyway it shares the base-name but increments the ending
