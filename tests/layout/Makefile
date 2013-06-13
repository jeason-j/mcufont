RENDER = ../../examples/render_bmp/render_bmp
INPUT = ../example_text.txt

TESTS = serif16_justified_500.bmp \
	serif16_left_500.bmp \
	serif16_right_500.bmp \
	serif16_center_500.bmp \
	fixed_7x14_left_600.bmp

all: $(TESTS) run_tests

clean:
	rm -f $(TESTS)

serif16_justified_500.bmp: OPTS = -f DejaVuSerif16 -w 500 -a j
serif16_left_500.bmp:      OPTS = -f DejaVuSerif16 -w 500 -a l
serif16_right_500.bmp:     OPTS = -f DejaVuSerif16 -w 500 -a r
serif16_center_500.bmp:    OPTS = -f DejaVuSerif16 -w 500 -a c
fixed_7x14_left_600.bmp:   OPTS = -f fixed_7x14 -w 600 -a l

%.bmp: $(RENDER) $(INPUT)
	$(RENDER) $(OPTS) -o $@ "`cat $(INPUT)`"

run_tests:
	@echo "Comparing the results to expected files.."
	@$(foreach test,$(TESTS),cmp $(test) $(test).expected &&) true

# Run this to copy the outputs as the new expected files.
update_expected: $(TESTS)
	@echo "Updating all the expected files.."
	@$(foreach test,$(TESTS),cp $(test) $(test).expected &&) true