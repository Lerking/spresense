############################################################################
# lte_awsiot/Makefile
#
#   Copyright 2019 Sony Corporation
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
# 1. Redistributions of source code must retain the above copyright
#    notice, this list of conditions and the following disclaimer.
# 2. Redistributions in binary form must reproduce the above copyright
#    notice, this list of conditions and the following disclaimer in
#    the documentation and/or other materials provided with the
#    distribution.
# 3. Neither the name of Sony Semiconductor Solutions Corporation nor
#    the names of its contributors may be used to endorse or promote
#    products derived from this software without specific prior written
#    permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
# FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE
# COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
# INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
# BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS
# OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED
# AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
# LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN
# ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
# POSSIBILITY OF SUCH DAMAGE.
#
############################################################################

-include $(TOPDIR)/Make.defs
-include $(SDKDIR)/Make.defs

# lte_awsiot built-in application info

CONFIG_EXAMPLES_LTE_AWSIOT_PRIORITY ?= SCHED_PRIORITY_DEFAULT
CONFIG_EXAMPLES_LTE_AWSIOT_STACKSIZE ?= 2048
CONFIG_EXAMPLES_LTE_AWSIOT_STACKSIZE_IN_USING_MBEDTLS ?= 5120

APPNAME = lte_awsiot
PRIORITY = $(CONFIG_EXAMPLES_LTE_AWSIOT_PRIORITY)
ifeq ($(CONFIG_EXTERNALS_MBEDTLS),y)
STACKSIZE = $(CONFIG_EXAMPLES_LTE_AWSIOT_STACKSIZE_IN_USING_MBEDTLS)
else
STACKSIZE = $(CONFIG_EXAMPLES_LTE_AWSIOT_STACKSIZE)
endif

# define

ifdef CONFIG_EXAMPLES_LTE_AWSIOT_IOT_DEBUG
 CFLAGS += -DENABLE_IOT_DEBUG
endif
ifdef CONFIG_EXAMPLES_LTE_AWSIOT_IOT_ERROR
 CFLAGS += -DENABLE_IOT_ERROR
endif

# lte_awsiot Example

ASRCS =
CSRCS += awsiot_lte_connection.c

# build AWS-IoT device SDK

include $(EXTERNAL_DIR)$(DELIM)awsiot$(DELIM)awsiot.mk

MAINSRC = subscribe_publish_sample.c

CONFIG_EXAMPLES_LTE_AWSIOT_PROGNAME ?= lte_awsiot$(EXEEXT)
PROGNAME = $(CONFIG_EXAMPLES_LTE_AWSIOT_PROGNAME)

include $(APPDIR)/Application.mk
