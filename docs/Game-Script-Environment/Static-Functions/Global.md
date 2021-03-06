---
sidebar_position: 1
title: Global
hide_title: true
sidebar-label: 'Global'
---

<br></br>

## Global Lua Namespace

Global functions.

## Functions

### class

```lua
class( base )
```

Creates a new class object.

<strong>Arguments:</strong> <br></br>

- <code>base</code> [<strong> class </strong>]: The base class to inherit from. Optional.

```lua title="Internal code of the class function"
function class(super)

	local klass = {}

	-- Copy members from super.
	if super then
		for k,v in pairs(super) do
			klass[k] = v
		end
	end

	local meta = {}

	-- Emulate constructor syntax.
	-- Triggers when a value is called like a function.
	meta.__call = function(self, ...)
		local instance = setmetatable({}, self)

		return instance
	end

	-- Emulate classes using prototyping.
	setmetatable(klass, meta)
	klass.__index = klass

	return klass
end
```

---

### dofile

```lua
dofile( filename )
```

Opens the named file and executes its contents as a Lua chunk. <br></br>
In case of errors, dofile propagates the error to its caller.

<strong>Arguments:</strong> <br></br>

- <code>filename</code> [<strong> string </strong>]: The name/path of the lua file to be loaded.

---

### print

```lua
print( ... )
```

Prints data to the console. This is useful for debugging.

:::info note
If the game is running with the <code>-dev</code> launch flag, any output will be added to the game logs.
:::

<strong>Arguments:</strong> <br></br>

- <code>...</code> [<strong> any </strong>]: Any number of arguments to be printed.

---

### type

```lua
type( object )
```

Returns the type of an object as a string. <br></br>
This includes standard Lua types and userdata types specific to this API.

<strong>Arguments:</strong> <br></br>

- <code>object</code> [<strong> any </strong>]: The object to check.

<strong>Returns:</strong> <br></br>

- [<strong> string </strong>]: The type of the object.

---

## Other Libraries

Listed below are all available default Lua libraries.

For documentation of these libraries, see the [Lua Reference Manual](https://www.lua.org/manual/5.1/manual.html).

### string
```lua
string.byte
string.char
string.find
string.format
string.gmatch
string.gsub
string.len
string.lower
string.match
string.rep
string.reverse
string.sub
string.upper
```

---

### table
```lua
table.insert
table.maxn
table.remove
table.sort
table.concat
```

---

### math
```lua
math.abs
math.acos
math.asin
math.atan
math.atan2
math.ceil
math.cos
math.cosh
math.deg
math.exp
math.floor
math.fmod
math.frexp
math.huge
math.ldexp
math.log
math.log10
math.max
math.min
math.modf
math.pi
math.pow
math.rad
math.random
math.sin
math.sinh
math.sqrt
math.tan
math.tanh
math.randomseed
```

---

### bit
```lua
bit.tobit
bit.tohex
bit.bnot
bit.band
bit.bor
bit.bxor
bit.lshift
bit.rshift
bit.arshift
bit.rol
bit.ror
bit.bswap
```

---

### os
```lua
os.clock
os.difftime
os.time
```

---

### other
```lua
assert
error
ipairs
next
pairs
pcall
select
tonumber
tostring
unpack
_VERSION
xpcall
gcinfo
```

---





