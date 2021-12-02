# Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0

HARNESS_FILE=skipAnyLiteral_harness
PROOF_UID=skipAnyLiteral

APPLY_LOOP_CONTRACTS=1

include ../Makefile-json.common

# Substitution command to pass to sed for patching core_json.c. The
# characters " and # must be escaped with backslash.
CORE_JSON_SED_EXPR = s/^static //

# We need to include the header file core_json_annex.h because skipCollection's
# loop invariant uses a macro from core_json_annex.h. Without this header file,
# CBMC will complain that skipCollection's loop invariant has a side effect. 
# This happens because, in the absence of the header file, the macro in
# skipCollection's loop invariant is interpreted as a function (rather than 
# a macro). 
CORE_JSON_SED_EXPR = s/^static //; 1s/^/\#include \"core_json_annex.h\" /
