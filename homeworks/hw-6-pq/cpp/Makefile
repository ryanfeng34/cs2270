# This top block is all you will probably need to change
STUDENT_IMPL_FILE 	= pq.cpp
STUDENT_OBJ_FILE 	= pq.o
PRIMARY_HEADER_FILE 	= pq.h
UNIT_TEST_IMPL_FILE 	= pq_driver.cpp
UNIT_TEST_OBJ_FILE 	= pq_driver.o
UNIT_TEST_BINARY 	= pq_driver

# Other object files needed in building targets for unit testing
FRAMEWORK_TARGETS	= UTFramework.o

USER_DIR = .
CPPFLAGS += -pthread -g -Wall -Wextra -std=c++0x

# House-keeping build targets.

all : $(UNIT_TEST_BINARY)

clean :
	rm -f $(TESTS) *.o $(UNIT_TEST_BINARY)

# Assignment-specific build rules below.

UTFramework.o: $(USER_DIR)/UTFramework.cpp	\
                 $(USER_DIR)/UTFramework.h
	$(CXX) $(CPPFLAGS) -c $(USER_DIR)/UTFramework.cpp

$(STUDENT_OBJ_FILE): $(USER_DIR)/$(STUDENT_IMPL_FILE) \
                $(USER_DIR)/$(PRIMARY_HEADER_FILE) \
                $(FRAMEWORK_TARGETS)
	$(CXX) $(CPPFLAGS) -c $(USER_DIR)/$(STUDENT_IMPL_FILE) -o $(STUDENT_OBJ_FILE)

$(UNIT_TEST_OBJ_FILE) : $(USER_DIR)/$(UNIT_TEST_IMPL_FILE) \
                     $(USER_DIR)/$(PRIMARY_HEADER_FILE) \
                     $(FRAMEWORK_TARGETS)
	$(CXX) $(CPPFLAGS) -c $(USER_DIR)/$(UNIT_TEST_IMPL_FILE)

$(UNIT_TEST_BINARY) : $(STUDENT_OBJ_FILE) $(UNIT_TEST_OBJ_FILE) \
		   $(FRAMEWORK_TARGETS)
	$(CXX) $(CPPFLAGS) $^ -o $@



