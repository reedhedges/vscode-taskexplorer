
# This makefile should result in these tasks under "make": clean, rule1, rule_2, rule-3, rule4, "multi target rule", program.exe

OBJS = $(CFILES:.c=.o)
clean:
	@echo make clean...
	rm -f $(OBJS) $(OBJS:.o=.d)
	rm -f *~

rule1:  rule2
	@echo rule1

rule_2 :
	@echo rule2

rule-3:
	@echo rule3 has command with : in it

# Repeated rules should be OK and result in only one task for that rule:
rule-3:
	@echo second version of rule3 has a command with : in it


# Double-colon rules should be treated the same:
rule4:: rule1
	@echo First rule4

rule4:: rule_2
	@echo Second rule4


# Should be skipped:
%.o: %.h
	@echo Pattern rule with file extension should be skipped

# Should be skipped:
%-foo:
	@echo This pattern rule should also be skipped

# Should not be skipped:
multi target rule: foo.o
	@echo multi target rule

# A Comment containing a :. This should be ignored (along with all other comments)

# Should not be skipped:
program.exe: foo.o bar.o
	@echo program.exe

# Wildcards in rules should be skipped:
*.x: 
	@echo This rule should be skipped

# All variable assignments below should be ignored.

VAR1=foo

VAR2:=foo

VAR3 := foo

# Uncomment this to trigger "already registered" error:
#ifdef FLAG
#VAR4:=foo
#VAR5 := foo
#else
#VAR4:=bar
#VAR5 := bar
#endif

# This should be ignored:
VAR6 = "String with a : in it"


# This shuold be ignored:
$(info testing : this is a test Makefile for the Task Explorer extension.)


.PHONY: clean rule1 rule_2 rule-3

