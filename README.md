# tmp.py

import json

def get(op):
	if op == 'add':
		return '+'
	if op == 'multiply':
		return '*'
	if op == 'divide':
		return '/'
	if op == 'subtract':
		return '-'
	if op == 'equal':
		return '='

def parse(jsn_obj):
	lhs = jsn_obj["lhs"]
	rhs = jsn_obj["rhs"]
	op = jsn_obj["op"]
	if type(lhs) == type(jsn_obj):
		lhs = parse(lhs)
	if type(rhs) == type(jsn_obj):
		rhs = parse(rhs)
	return  "(" + str(lhs) + " " + get(op) + " " + str(rhs) + ")"


f = open("expression.json","r")
dom = json.load(f)

print parse(dom)
