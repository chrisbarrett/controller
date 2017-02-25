GITROOT := $(shell git rev-parse --show-toplevel)
LAYOUTS := $(GITROOT)/kll/layouts

# These are in the 'kll' submodule.
SOURCES := mdergo1Overlay.kll lcdFuncMap.kll iced_func.kll iced_numpad.kll
SOURCES := $(addprefix $(LAYOUTS)/, $(SOURCES))

LEFT  := ICED-L.gcc
RIGHT := ICED-R.gcc

.PHONY: help left right clean

help:
	@echo Usage:
	@echo '    make [left|right|clean|help]'
	@echo
	@echo The two ergodox sides must be flashed separately. Connect the side to
	@echo be flashed, then run the corresponding make task.
	@echo
	@echo Tasks:
	@echo '    left     Build and flash the attached left-hand keyboard.'
	@echo '    right    Build and flash the attached right-hand keyboard.'
	@echo '    clean    Clean generated code.'
	@echo '    help     Show this message.'

clean:
	rm -fr $(LEFT) $(RIGHT)

left : $(LEFT)
	cd $(LEFT) && (timeout 6 ./load || true)

right : $(RIGHT)
	cd $(RIGHT) && (timeout 6 ./load || true)

$(LEFT) $(RIGHT): $(SOURCES)
	./ergodox.bash
