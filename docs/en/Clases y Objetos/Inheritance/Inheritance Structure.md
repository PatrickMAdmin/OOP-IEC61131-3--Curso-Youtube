## <span style="color:grey">Structure Inheritance:</span>

Like the functions blocks, the structures can be expanded.The structure then obtains the variables of the basic structure in addition to its own variables.

Create a structure that extends to another structure:
```javascript
TYPE ST_Base1 :
STRUCT
	bBool1: BOOL;
	iINT : INT;
	rReal : REAL;	
END_STRUCT
END_TYPE
```
```javascript
TYPE ST_Sub1 EXTENDS ST_Base1:
STRUCT
	ttime :TIME;
	tton  : TON;
END_STRUCT
END_TYPE
```
```javascript
TYPE ST_Sub2 EXTENDS ST_Sub1 :
STRUCT
	bBool2: BOOL; // You could not call the bBool1 variable because we have it declared in the St_Base1 structure
END_STRUCT
END_TYPE
```
```javascript
PROGRAM MAIN
VAR
    stestructura1  : ST_Sub1;
    stestructura2  : ST_Sub2;
END_VAR

//Structure extension:
stestructura1.bBool1;
stestructura1.iINT;
stestructura1.rReal;
stestructura1.ttime;
stestructura1.tton(in:= TRUE, pt:=T#1S);

stestructura2.bBool1;
stestructura2.iINT;
stestructura2.rReal;
stestructura2.ttime;
stestructura2.tton(in:= TRUE, pt:=T#1S);
stestructura2.bBool2;
```

- In this way of extending an inheritance structure, the same variable name declared with the extended structures cannot be repeated.

- Also without using extends for the structure we could do it as follows:

```javascript
TYPE ST_2 :
STRUCT
	bBool : BOOL;
END_STRUCT
END_TYPE
```
```javascript
TYPE ST_1:
STRUCT
	sStruct : ST_2;
	sstring : STRING(80);
END_STRUCT
END_TYPE
```
```javascript
PROGRAM MAIN
VAR
	stestructura11 : ST_1;
END_VAR

stestructura11.sstring;
stestructura11.sStruct.bBool; //The result is that it is more nested
```

- In this way, the same name of the variable in different structures can be declared, since the previous problem is nested.

- Multiple inheritance is not allowed as follows:

```javascript
TYPE ST_Sub EXTENDS ST_Base1,ST_Base2 :
STRUCT
```
***
### <span style="color:grey">Links:</span>

- 🔗 [infosys.beckhoff.com, Extends Structure](https://infosys.beckhoff.com/content/1033/tc3_plc_intro/3468091787.html?id=592001323464924565)

- 🔗 [help.codesys.com, Structure](https://help.codesys.com/webapp/_cds_datatype_structure;product=codesys;version=3.5.17.0)

- 🔗 [help.codesys.com, Structure](https://help.codesys.com/api-content/2/codesys/3.5.14.0/en/_cds_obj_dut/)

- 🔗 [help.codesys.com, Structure](https://help.codesys.com/api-content/2/codesys/3.5.14.0/en/_cds_datatype_structure/#b2e3e6da93f532b0c0a8640e011c7a1d-3s-structures)

***
### <span style="color:grey">Link to the Youtube Video 008:</span>
- 🔗 [008 - OOP IEC 61131-3 PLC -- Herencia Estructura e Interface](https://youtu.be/G0suYh_bz0o)
