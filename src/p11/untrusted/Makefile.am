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

noinst_DATA = p11Enclave_u.c p11Enclave_u.h

EXTRA_DIST = $(srcdir)/../include/*.h \
             $(srcdir)/../enclave_config/*.xml \
             $(srcdir)/../enclave_config/*.pem \
             $(srcdir)/../enclave_config/*.edl
AM_CPPFLAGS = -I$(SGXSDKDIR)/include -I$(srcdir)/../include
AM_CXXFLAGS = -D_FORTIFY_SOURCE=2 -std=c++11 -fstack-protector -Wformat -Wformat-security -fpie -fpic -fexceptions -fno-strict-overflow -fno-delete-null-pointer-checks -fwrapv
AM_CFLAGS = -D_FORTIFY_SOURCE=2 -fvisibility=hidden -fpie -fpic -fstack-protector -Wformat -Wformat-security -std=c11 -fexceptions -fno-strict-overflow -fno-delete-null-pointer-checks -fwrapv

AM_LDFLAGS = -L$(SGXSSLDIR)/lib64 -lsgx_usgxssl -L$(SGXSDKDIR)/lib64 -lsgx_urts -lsgx_uae_service \
             -Wl,-z,noexecstack -Wl,-z,relro -Wl,-z,now -pie -export-dynamic -module -shared

lib_LTLIBRARIES = libp11sgx.la
libp11sgx_la_SOURCES =  p11Enclave_u.c \
                        p11Enclave_u.h \
                        AttributeHelpers.h \
                        AttributeHelpers.cpp \
                        AttributeCache.h \
                        AttributeCache.cpp \
                        AsymmetricKeyHandleCache.cpp \
                        AsymmetricKeyHandleCache.h \
                        AsymmetricProvider.cpp \
                        AsymmetricProvider.h \
                        EnclaveHelpers.cpp \
                        EnclaveHelpers.h \
                        HashHandleCache.cpp \
                        HashHandleCache.h \
                        HashProvider.cpp \
                        HashProvider.h \
                        P11Provider.cpp \
                        SessionHandleCache.cpp \
                        SessionHandleCache.h \
                        SymmetricKeyHandleCache.cpp \
                        SymmetricKeyHandleCache.h \
                        SymmetricProvider.cpp \
                        SymmetricProvider.h \
                        Slot.h \
                        Slot.cpp \
                        Token.h \
                        Token.cpp

p11Enclave_u.h: p11Enclave_u.c

p11Enclave_u.c:
	$(SGX_EDGER8R) --untrusted p11Enclave.edl --search-path $(srcdir)/../include --search-path $(srcdir)/../enclave_config --search-path $(SGXSDKDIR)/include --search-path $(SGXSSLDIR)/include

clean-local:
	test -z *.la || rm -rf *.la
	test -z p11Enclave_u.c || rm -rf p11Enclave_u.c
	test -z p11Enclave_u.h || rm -rf p11Enclave_u.h
	test -z *.lo || rm -rf *.lo
