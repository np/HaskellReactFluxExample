.PHONY: all clean
INSTALL_ROOT:=$(shell stack path --local-install-root)

# all: js-build/install-root js-build/frontend.min.js
all: js-build/install-root js-build/frontend.js

js-build/install-root: $(INSTALL_ROOT)
	mkdir -p js-build
	ln -sf $(INSTALL_ROOT) js-build/install-root

js-build/frontend.min.js: js-build/frontend.js
	closure --compilation_level=ADVANCED_OPTIMIZATIONS js-build/frontend.js > js-build/frontend.min.js

js-build/frontend.js: $(INSTALL_ROOT)/bin/frontend.jsexe/all.js
	mkdir -p js-build
	echo "(function(global,React,ReactDOM) {" > js-build/frontend.js
	cat $(INSTALL_ROOT)/bin/frontend.jsexe/all.js >> js-build/frontend.js
	echo "})(window, window['React'], window['ReactDOM']);" >> js-build/frontend.js
	sed -i 's/goog.provide.*//' js-build/frontend.js
	sed -i 's/goog.require.*//' js-build/frontend.js

clean:
	rm -rf js-build

hlint:
	test -e ~/.cabal/bin/hlint || cabal install hlint
	~/.cabal/bin/hlint src/
