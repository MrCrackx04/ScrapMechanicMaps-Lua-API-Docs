---
sidebar_position: 2
title: Environment Table
hide_title: true
sidebar-label: 'Environment Table'
---

<br></br>

## Environment Table

This is the raw Lua environment table of the game script environment.

```lua
unsafe_env = {
	print = print,
	dofile = dofile,
	type = type,
	assert = assert,
	error = error,
	ipairs = ipairs,
	next = next,
	pairs = pairs,
	pcall = pcall,
	select = select,
	tonumber = tonumber,
	tostring = tostring,
	type = type,
	unpack = unpack,
	_VERSION = _VERSION,
	xpcall = xpcall,
	gcinfo = gcinfo,
	class = class,
	sm = {
		version = sm.version,
		isHost = sm.isHost,
		isServerMode = sm.isServerMode,
		exists = sm.exists,
		color = sm.color,
		uuid = sm.uuid,
		projectile = sm.projectile,
		creation = sm.creation,
		interactable = sm.interactable,
		audio = sm.audio,
		body = sm.body,
		effect = sm.effect,
		builderGuide = sm.builderGuide,
		cullSphereGroup = sm.cullSphereGroup,
		particle = sm.particle,
		debris = sm.debris,
		noise = sm.noise,
		quat = sm.quat,
		physics = sm.physics,
		vec3 = sm.vec3,
		camera = sm.camera,
		localPlayer = sm.localPlayer,
		tool = sm.tool,
		shape = sm.shape,
		util = sm.util,
		storage = sm.storage,
		network = sm.network,
		raycastResult = sm.raycastResult,
		container = sm.container,
		json = sm.json,
		gui = sm.gui,
		player = sm.player,
		character = sm.character,
		joint = sm.joint,
		world = sm.world,
		areaTrigger = sm.areaTrigger,
		game = sm.game,
		cell = sm.cell,
		event = sm.event,
		visualization = sm.visualization,
		challenge = sm.challenge,
		menuCreation = sm.menuCreation,
		log = sm.log,
		item = sm.item,
		harvestable = sm.harvestable,
		unit = sm.unit,
		pathfinder = sm.pathfinder,
		pathNode = sm.pathNode,
		lift = sm.lift,
		portal = sm.portal,
		render = sm.render,
		melee = sm.melee,
		debugDraw = sm.debugDraw,
		ai = sm.ai,
		construction = sm.construction,
		scriptableObject = sm.scriptableObject
	},
	string = {
		byte = string.byte,
		char = string.char,
		find = string.find,
		format = string.format,
		gmatch = string.gmatch,
		gsub = string.gsub,
		len = string.len,
		lower = string.lower,
		match = string.match,
		rep = string.rep,
		reverse = string.reverse,
		sub = string.sub,
		upper = string.upper
	},
	table = {
		insert = table.insert,
		maxn = table.maxn,
		remove = table.remove,
		sort = table.sort,
		concat = table.concat
	},
	math = {
		abs = math.abs,
		acos = math.acos,
		asin = math.asin,
		atan = math.atan,
		atan2 = math.atan2,
		ceil = math.ceil,
		cos = math.cos,
		cosh = math.cosh,
		deg = math.deg,
		exp = math.exp,
		floor = math.floor,
		fmod = math.fmod,
		frexp = math.frexp,
		huge = math.huge,
		ldexp = math.ldexp,
		log = math.log,
		log10 = math.log10,
		max = math.max,
		min = math.min,
		modf = math.modf,
		pi = math.pi,
		pow = math.pow,
		rad = math.rad,
		random = math.random,
		sin = math.sin,
		sinh = math.sinh,
		sqrt = math.sqrt,
		tan = math.tan,
		tanh = math.tanh
	},
	bit = {
		tobit = bit.tobit,
		tohex = bit.tohex,
		bnot = bit.bnot,
		band = bit.band,
		bor = bit.bor,
		bxor = bit.bxor,
		lshift = bit.lshift,
		rshift = bit.rshift,
		arshift = bit.arshift,
		rol = bit.rol,
		ror = bit.ror,
		bswap = bit.bswap
	},
	os = {
		clock = os.clock,
		difftime = os.difftime,
		time = os.time
	}
}
```












