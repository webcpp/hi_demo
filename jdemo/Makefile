
SRC=$(shell echo `find . -type f | egrep *.java$$`)
OBJ=$(patsubst %.java,%.class,$(SRC))

ifndef NGINX_INSTALL_DIR
NGINX_INSTALL_DIR=/usr/local/nginx
endif

JFLAGS = -classpath .:${NGINX_INSTALL_DIR}/java/hi-nginx-java.jar
JC = ${JAVA_HOME}/bin/javac

%.class:%.java
	$(JC) $(JFLAGS) $^


default: classes


classes:$(OBJ)

clean:
	rm -f ${OBJ}

install:${OBJ}
	for i in ${OBJ};do test -d $(NGINX_INSTALL_DIR)/java/`dirname $$i` || mkdir -p $(NGINX_INSTALL_DIR)/java/`dirname $$i` && install $$i $(NGINX_INSTALL_DIR)/java/$$i ;done



