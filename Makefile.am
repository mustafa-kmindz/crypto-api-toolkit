#
# Copyright (C) 2019 Intel Corporation. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
#   * Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#   * Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in
#     the documentation and/or other materials provided with the
#     distribution.
#   * Neither the name of Intel Corporation nor the names of its
#     contributors may be used to endorse or promote products derived
#     from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#
#

EXTRA_DIST = $(srcdir)/src/p11/include/Constants.h \
             $(srcdir)/src/p11/include/p11Defines.h \
             $(srcdir)/src/p11/include/pkcs11.h \
             $(srcdir)/src/p11/include/pkcs11f.h \
             $(srcdir)/src/p11/include/pkcs11t.h \
             $(srcdir)/src/p11/enclave_config/p11Enclave.config.xml \
             $(srcdir)/src/p11/enclave_config/p11Enclave.edl \
             $(srcdir)/src/p11/enclave_config/p11Enclave.pem \
             $(srcdir)/src/p11/enclave_config/p11Enclave_private.pem

dist-hook:
	rm -f $(distdir)/src/p11/trusted/p11Enclave_t*
	rm -f $(distdir)/src/p11/untrusted/p11Enclave_u*

SUBDIRS = src

install-exec-local:
	mkdir -p $(CATKTOKENPATH)/tokens
	chmod -R 1777 $(CATKTOKENPATH)/tokens