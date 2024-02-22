include ../.env

RESOURCE_PACKS=My_RESOURCE_Pack My_RESOURCE_Pack2
BEHAVIOR_PACKS=My_BEHAVIOR_Pack

TARGET=My_RESOURCE_Pack.mcpack My_BEHAVIOR_Pack.mcpack

.PHONY: all
all: install

.PHONY: install install/resource install/behavior
install: install/resource install/behavior
install/resource: $(RESOURCE_PACKS:%=install/resource/%)
install/behavior: $(BEHAVIOR_PACKS:%=install/behavior/%)
install/resource/%: DESTINATION = $(COM_MOJANG)/development_resource_packs
install/behavior/%: DESTINATION = $(COM_MOJANG)/development_behavior_packs
install/%: clean/%
	$(if $(value DESTINATION),,$(error DESTINATION is not set))
	cp -r $(lastword $(subst /, ,$@)) $(DESTINATION)
$(RESOURCE_PACKS:%=install/resource/%) $(BEHAVIOR_PACKS:%=install/behavior/%):

.PHONY: mcpack
mcpack: $(RESOURCE_PACKS:%=%.mcpack) $(BEHAVIOR_PACKS:%=%.mcpack)
%.mcpack: %/*
	zip $@ $^
$(RESOURCE_PACKS:%=%.mcpack) $(BEHAVIOR_PACKS:%=%.mcpack):

.PHONY: clean clean/resource clean/behavior clean/mcpack
clean: clean/resource clean/behavior clean/mcpack
clean/resource: $(RESOURCE_PACKS:%=clean/resource/%)
clean/behavior: $(BEHAVIOR_PACKS:%=clean/behavior/%)
clean/resource/%: DESTINATION = $(COM_MOJANG)/development_resource_packs
clean/behavior/%: DESTINATION = $(COM_MOJANG)/development_behavior_packs
clean/%:
	$(if $(value DESTINATION),,$(error DESTINATION is not set))
	rm -rf $(DESTINATION)/$(lastword $(subst /, ,$@))
$(RESOURCE_PACKS:%=clean/resource/%) $(BEHAVIOR_PACKS:%=clean/behavior/%):
clean/mcpack:
	rm -f *.mcpack

uuidgen:
	uuidgen
