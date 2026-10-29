# Third-party notices

redPeaRL includes software from the projects below. Their copyright and permission notices are reproduced as their licences require. redPeaRL itself is proprietary software of Red PeaRL Miner (see LICENSE).

## tnn-miner

redPeaRL was built from tnn-miner (https://github.com/Tritonn204/tnn-miner), commit b567a87, which provided the initial source of the Pearl GPU engine, the stratum and pool code and the miner framework.

```
MIT License

Copyright (c) 2023 Tritonn204

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Orochi

contrib/Orochi - runtime HIP/CUDA loader.

```
MIT License

Copyright (c) 2022 Advanced Micro Devices, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Pearl reference algorithms

src/rpm_hip/crypto/pearl - native implementation following the Pearl reference algorithms.

```
Reference algorithms: Pearl pearl-blake3/src/merkle.rs and
zk-pow/src/circuit/pearl_noise.rs, https://github.com/pearl-research-labs/pearl
The native C++ implementation is
independently structured and preserves the reference wire/math contract.

ISC License

Copyright (c) 2025-2026 Pearl Research Labs
Copyright (c) 2015-2016 The Decred developers

Permission to use, copy, modify, and distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

## libkeccak

include/libkeccak - Keccak / SHA-3 / cSHAKE implementation by Mattias Andrée.

```
ISC License

© 2014, 2015, 2017, 2019, 2021, 2022, 2024, 2026 Mattias Andrée <m@maandree.se>

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

## Orochi runtime loader (hipew)

contrib/Orochi/contrib/hipew - Copyright 2011-2021 Blender Foundation.
Licensed under the Apache License, Version 2.0 (text below).

## AMD SMI for WSL (Linux package and container image only)

lib/libamd_smi.so.1 in the Linux package and the container image - rocdxg-amd-smi-lib 1.2.2, a WSL build of AMD SMI
(https://github.com/ROCm/librocdxg, upstream https://github.com/ROCm/amdsmi). Copyright (c) Advanced Micro Devices,
Inc. MIT License (text as for Orochi above, with that copyright line; also shipped as lib/LICENSE-amd-smi.txt). Loaded
at run time for GPU sensors under WSL2; not part of the Windows package.

## AMD Display Library SDK header

include/adl_defines.h - Copyright (c) 2016 - 2022 Advanced Micro Devices, Inc. MIT License (text as for
Orochi above, with that copyright line).

## BLAKE3

extern/BLAKE3 - the BLAKE3 reference implementation, released into the public domain under CC0 1.0, or
alternatively under the Apache License 2.0.
The CC0 1.0 Universal legal code is in extern/BLAKE3/c/LICENSE_CC0.

## base64 (Tobias Locker)

include/base64.hpp - base64 encoder/decoder, https://github.com/tobiaslocker/base64, MIT License.
The header below is the one the original file carries; the copy inherited from tnn-miner had lost it and it
was restored on 10 Oct 2026.

```
/*
MIT License

Copyright (c) 2019 Tobias Locker

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
```

## Skein

src/crypto/skein - Skein hash reference implementation, released into the public domain by its authors.

## winpthreads (Windows build)

mingw-w64 winpthreads, statically linked into the Windows exe.

```
Copyright (c) 2011 mingw-w64 project

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the "Software"),
to deal in the Software without restriction, including without limitation
the rights to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.
```

## OpenSSL

OpenSSL 3 (statically linked) - Copyright (c) 1998-2025 The OpenSSL Project Authors. Licensed under the
Apache License, Version 2.0 (text below).

## Boost

Boost C++ Libraries (statically linked) - Boost Software License 1.0.

```
Boost Software License - Version 1.0 - August 17th, 2003

Permission is hereby granted, free of charge, to any person or organization
obtaining a copy of the software and accompanying documentation covered by
this license (the "Software") to use, reproduce, display, distribute,
execute, and transmit the Software, and to prepare derivative works of the
Software, and to permit third-parties to whom the Software is furnished to
do so, all subject to the following:

The copyright notices in the Software and this entire statement, including
the above license grant, this restriction and the following disclaimer,
must be included in all copies of the Software, in whole or in part, and
all derivative works of the Software, unless such copies or derivative
works are solely in the form of machine-executable object code generated by
a source language processor.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. IN NO EVENT
SHALL THE COPYRIGHT HOLDERS OR ANYONE DISTRIBUTING THE SOFTWARE BE LIABLE
FOR ANY DAMAGES OR OTHER LIABILITY, WHETHER IN CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.
```

## redpearl-app.exe (the desktop app)

The desktop app is a separate program in the package, written in Rust on the Tauri 2 framework (MIT OR Apache-2.0,
Copyright (c) 2017-present Tauri Programme within The Commons Conservancy). It shows its pages in Microsoft Edge
WebView2, which is part of Windows 10/11 and is not redistributed here. Where a crate offers a choice of licence we take
it under the MIT License (text above); where MIT is not offered, under the Apache License 2.0 (text below) or the
licence named. The Unicode data crates are used under the Unicode License v3 (text below); the webpki-roots root
certificate store under CDLA-Permissive-2.0 (text at https://cdla.dev/permissive-2-0/). Five crates of Tauri's CSS
and selector stack are under the Mozilla Public License 2.0: cssparser, cssparser-macros, dtoa-short, option-ext,
selectors - used unmodified, their source is available from https://crates.io, and the licence text is at
https://mozilla.org/MPL/2.0/.

Crates linked into redpearl-app.exe (`cargo tree -e normal --target x86_64-pc-windows-msvc`, 225 packages,
26 Oct 2026; each is used unmodified from crates.io under the licence its authors declared):

- **MIT OR Apache-2.0** (113): anyhow 1.0.104, base64 0.22.1, base64 0.23.1, bitflags 2.13.2, block-buffer 0.10.4, camino 1.2.6, cargo-platform 0.1.9, cfg-if 1.0.5, cookie 0.18.2, cpufeatures 0.2.17, crc32fast 1.5.3, crossbeam-channel 0.5.17, crossbeam-utils 0.8.23, crypto-common 0.1.7, deranged 0.5.9, digest 0.10.7, dirs 7.0.0, dirs-sys 0.5.0, displaydoc 0.2.7, dtoa 1.0.11, dyn-clone 1.0.20, erased-serde 0.4.10, fdeflate 0.3.7, flate2 1.1.10, form_urlencoded 1.2.2, getrandom 0.2.17, getrandom 0.3.4, getrandom 0.4.3, glob 0.3.4, hashbrown 0.12.3, hashbrown 0.17.1, heck 0.5.0, html5ever 0.39.0, http 1.5.0, idna 1.1.0, itoa 1.0.18, jsonptr 0.7.1, keyboard-types 0.8.3, libc 0.2.191, lock_api 0.4.14, log 0.4.34, markup5ever 0.39.0, mime 0.3.17, num-conv 0.2.2, once_cell 1.21.4, parking_lot 0.12.5, parking_lot_core 0.9.12, percent-encoding 2.3.2, png 0.18.1, powerfmt 0.2.1, proc-macro2 1.0.107, quote 1.0.47, regex 1.13.1, regex-automata 0.4.18, regex-syntax 0.8.11, rustls-pki-types 1.15.1, scopeguard 1.2.0, semver 1.0.28, serde 1.0.229, serde-untagged 0.1.9, serde_core 1.0.229, serde_derive 1.0.229, serde_derive_internals 0.29.1, serde_json 1.0.154, serde_repr 0.1.21, serde_spanned 1.1.2, serde_with 3.24.0, serde_with_macros 3.24.0, serialize-to-javascript 0.1.2, serialize-to-javascript-impl 0.1.2, servo_arc 0.4.3, sha2 0.10.9, siphasher 1.0.4, smallvec 1.16.3, socket2 0.6.5, softbuffer 0.4.8, stable_deref_trait 1.2.1, string_cache 0.9.0, syn 2.0.119, syn 3.0.9, tendril 0.5.1, thiserror 2.0.21, thiserror-impl 2.0.21, time 0.3.55, time-core 0.1.9, time-macros 0.2.32, toml 1.1.8+spec-1.1.0, toml_datetime 1.1.2+spec-1.1.0, toml_parser 1.1.5+spec-1.1.0, toml_writer 1.1.3+spec-1.1.0, typeid 1.0.3, typenum 1.20.1, unicode-segmentation 1.13.3, ureq 2.12.1, url 2.5.8, web-time 1.1.0, web_atoms 0.2.6, windows 0.62.2, windows-collections 0.3.2, windows-core 0.62.2, windows-future 0.3.2, windows-implement 0.60.2, windows-interface 0.59.3, windows-link 0.2.1, windows-numerics 0.3.1, windows-result 0.4.1, windows-strings 0.5.1, windows-sys 0.59.0, windows-sys 0.61.2, windows-targets 0.52.6, windows-threading 0.2.1, windows-version 0.1.7, windows_x86_64_msvc 0.52.6
- **MIT** (36): bytes 1.12.1, cargo_metadata 0.19.2, cfb 0.14.0, darling 0.24.1, darling_core 0.24.1, darling_macro 0.24.1, derive_more 2.1.1, derive_more-impl 2.1.1, dom_query 0.28.0, generic-array 0.14.7, ico 0.6.0, infer 0.22.0, mio 1.2.4, new_debug_unreachable 1.0.6, phf 0.13.1, phf_generator 0.13.1, phf_macros 0.13.1, phf_shared 0.13.1, plist 1.10.3, precomputed-hash 0.1.1, quick-xml 0.42.0, schemars 0.8.22, schemars_derive 0.8.22, simd-adler32 0.3.10, strsim 0.11.1, synstructure 0.14.0, tokio 1.54.1, tracing 0.1.44, tracing-attributes 0.1.31, tracing-core 0.1.36, urlpattern 0.6.0, webview2-com 0.39.1, webview2-com-macros 0.8.1, webview2-com-sys 0.39.1, winnow 1.0.4, zmij 1.0.23
- **Apache-2.0 OR MIT** (24): bit-set 0.8.0, bit-vec 0.8.0, ctor 1.0.13, equivalent 1.0.3, fastrand 2.5.0, idna_adapter 1.2.2, indexmap 1.9.3, indexmap 2.14.2, muda 0.20.0, pin-project-lite 0.2.17, rustc-hash 2.1.3, tauri 2.12.5, tauri-codegen 2.7.4, tauri-macros 2.7.4, tauri-plugin-single-instance 2.5.4, tauri-plugin-window-state 2.5.0, tauri-runtime 2.12.2, tauri-runtime-wry 2.12.3, tauri-utils 2.10.2, utf8_iter 1.0.4, uuid 1.28.0, window-vibrancy 0.8.1, wry 0.57.0, zeroize 1.9.1
- **Unicode-3.0** (18): icu_collections 2.4.0, icu_locale_core 2.4.0, icu_normalizer 2.4.0, icu_normalizer_data 2.4.0, icu_properties 2.4.0, icu_properties_data 2.4.0, icu_provider 2.4.0, litemap 0.8.3, potential_utf 0.1.6, tinystr 0.8.5, writeable 0.6.4, yoke 0.8.4, yoke-derive 0.8.4, zerofrom 0.1.8, zerofrom-derive 0.1.8, zerotrie 0.2.5, zerovec 0.11.9, zerovec-derive 0.11.7
- **MPL-2.0** (5): cssparser 0.37.0, cssparser-macros 0.7.1, dtoa-short 0.3.5, option-ext 0.2.0, selectors 0.38.0
- **Unlicense OR MIT** (4): aho-corasick 1.1.5, byteorder 1.5.0, memchr 2.8.3, winapi-util 0.1.11
- **BSD-3-Clause** (3): alloc-no-stdlib 3.0.0, alloc-stdlib 0.3.0, subtle 2.6.1
- **MIT/Apache-2.0** (2): ident_case 1.0.1, json-patch 4.2.0
- **MIT OR Zlib OR Apache-2.0** (2): miniz_oxide 0.8.9, miniz_oxide 0.9.1
- **ISC** (2): rustls-webpki 0.103.16, untrusted 0.9.0
- **Unlicense/MIT** (2): same-file 1.0.6, walkdir 2.5.0
- **CDLA-Permissive-2.0** (2): webpki-roots 0.26.11, webpki-roots 1.0.10
- **0BSD OR MIT OR Apache-2.0** (1): adler2 2.0.1
- **BSD-3-Clause AND MIT** (1): brotli 9.0.0
- **BSD-3-Clause/MIT** (1): brotli-decompressor 6.0.1
- **Apache-2.0 AND MIT** (1): dpi 0.1.2
- **CC0-1.0 OR MIT-0 OR Apache-2.0** (1): dunce 1.0.5
- **Apache-2.0 / MIT** (1): fnv 1.0.7
- **Zlib** (1): foldhash 0.2.0
- **MIT OR Apache-2.0 OR Zlib** (1): raw-window-handle 0.6.2
- **Apache-2.0 AND ISC** (1): ring 0.17.14
- **Apache-2.0 OR ISC OR MIT** (1): rustls 0.23.46
- **Apache-2.0** (1): tao 0.37.1
- **(MIT OR Apache-2.0) AND Unicode-3.0** (1): unicode-ident 1.0.27


### BSD-3-Clause (alloc-no-stdlib, alloc-stdlib, subtle, brotli, brotli-decompressor)

```
Redistribution and use in source and binary forms, with or without modification, are permitted provided that the
following conditions are met:
1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following
   disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following
   disclaimer in the documentation and/or other materials provided with the distribution.
3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote
   products derived from this software without specific prior written permission.
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES,
INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

### ISC License (rustls-webpki, untrusted, ring in part)

```
Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby
granted, provided that the above copyright notice and this permission notice appear in all copies.
THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT,
INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN
AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
PERFORMANCE OF THIS SOFTWARE.
```

### zlib License (foldhash)

```
This software is provided 'as-is', without any express or implied warranty. In no event will the authors be held
liable for any damages arising from the use of this software.
Permission is granted to anyone to use this software for any purpose, including commercial applications, and to
alter it and redistribute it freely, subject to the following restrictions:
1. The origin of this software must not be misrepresented; you must not claim that you wrote the original software.
   If you use this software in a product, an acknowledgment in the product documentation would be appreciated but is
   not required.
2. Altered source versions must be plainly marked as such, and must not be misrepresented as being the original
   software.
3. This notice may not be removed or altered from any source distribution.
```

### Unicode License v3 (the icu_* data and support crates, litemap, potential_utf, tinystr, writeable, yoke, zerofrom, zerotrie, zerovec, unicode-ident in part)

```
UNICODE LICENSE V3

COPYRIGHT AND PERMISSION NOTICE

Copyright (c) 1991-2024 Unicode, Inc.

NOTICE TO USER: Carefully read the following legal agreement. BY DOWNLOADING, INSTALLING, COPYING OR OTHERWISE USING
DATA FILES, AND/OR SOFTWARE, YOU UNEQUIVOCALLY ACCEPT, AND AGREE TO BE BOUND BY, ALL OF THE TERMS AND CONDITIONS OF
THIS AGREEMENT. IF YOU DO NOT AGREE, DO NOT DOWNLOAD, INSTALL, COPY, DISTRIBUTE OR USE THE DATA FILES OR SOFTWARE.

Permission is hereby granted, free of charge, to any person obtaining a copy of data files and any associated
documentation (the "Data Files") or software and any associated documentation (the "Software") to deal in the Data
Files or Software without restriction, including without limitation the rights to use, copy, modify, merge, publish,
distribute, and/or sell copies of the Data Files or Software, and to permit persons to whom the Data Files or Software
are furnished to do so, provided that either (a) this copyright and permission notice appear with all copies of the
Data Files or Software, or (b) this copyright and permission notice appear in associated Documentation.

THE DATA FILES AND SOFTWARE ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT
LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT OF THIRD PARTY
RIGHTS. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR HOLDERS INCLUDED IN THIS NOTICE BE LIABLE FOR ANY CLAIM, OR ANY
SPECIAL INDIRECT OR CONSEQUENTIAL DAMAGES, OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS,
WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE
OR PERFORMANCE OF THE DATA FILES OR SOFTWARE.

Except as contained in this notice, the name of a copyright holder shall not be used in advertising or otherwise to
promote the sale, use or other dealings in these Data Files or Software without prior written authorization of the
copyright holder.
```

## Apache License 2.0

Applies to OpenSSL and hipew as stated above.

```
                                 Apache License
                           Version 2.0, January 2004
                        https://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      copyright notice that is included in or attached to the work
      (an example is provided in the Appendix below).

      "Derivative Works" shall mean any work, whether in Source or Object
      form, that is based on (or derived from) the Work and for which the
      editorial revisions, annotations, elaborations, or other modifications
      represent, as a whole, an original work of authorship. For the purposes
      of this License, Derivative Works shall not include works that remain
      separable from, or merely link (or bind by name) to the interfaces of,
      the Work and Derivative Works thereof.

      "Contribution" shall mean any work of authorship, including
      the original version of the Work and any modifications or additions
      to that Work or Derivative Works thereof, that is intentionally
      submitted to Licensor for inclusion in the Work by the copyright owner
      or by an individual or Legal Entity authorized to submit on behalf of
      the copyright owner. For the purposes of this definition, "submitted"
      means any form of electronic, verbal, or written communication sent
      to the Licensor or its representatives, including but not limited to
      communication on electronic mailing lists, source code control systems,
      and issue tracking systems that are managed by, or on behalf of, the
      Licensor for the purpose of discussing and improving the Work, but
      excluding communication that is conspicuously marked or otherwise
      designated in writing by the copyright owner as "Not a Contribution."

      "Contributor" shall mean Licensor and any individual or Legal Entity
      on behalf of whom a Contribution has been received by Licensor and
      subsequently incorporated within the Work.

   2. Grant of Copyright License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      copyright license to reproduce, prepare Derivative Works of,
      publicly display, publicly perform, sublicense, and distribute the
      Work and such Derivative Works in Source or Object form.

   3. Grant of Patent License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      (except as stated in this section) patent license to make, have made,
      use, offer to sell, sell, import, and otherwise transfer the Work,
      where such license applies only to those patent claims licensable
      by such Contributor that are necessarily infringed by their
      Contribution(s) alone or by combination of their Contribution(s)
      with the Work to which such Contribution(s) was submitted. If You
      institute patent litigation against any entity (including a
      cross-claim or counterclaim in a lawsuit) alleging that the Work
      or a Contribution incorporated within the Work constitutes direct
      or contributory patent infringement, then any patent licenses
      granted to You under this License for that Work shall terminate
      as of the date such litigation is filed.

   4. Redistribution. You may reproduce and distribute copies of the
      Work or Derivative Works thereof in any medium, with or without
      modifications, and in Source or Object form, provided that You
      meet the following conditions:

      (a) You must give any other recipients of the Work or
          Derivative Works a copy of this License; and

      (b) You must cause any modified files to carry prominent notices
          stating that You changed the files; and

      (c) You must retain, in the Source form of any Derivative Works
          that You distribute, all copyright, patent, trademark, and
          attribution notices from the Source form of the Work,
          excluding those notices that do not pertain to any part of
          the Derivative Works; and

      (d) If the Work includes a "NOTICE" text file as part of its
          distribution, then any Derivative Works that You distribute must
          include a readable copy of the attribution notices contained
          within such NOTICE file, excluding those notices that do not
          pertain to any part of the Derivative Works, in at least one
          of the following places: within a NOTICE text file distributed
          as part of the Derivative Works; within the Source form or
          documentation, if provided along with the Derivative Works; or,
          within a display generated by the Derivative Works, if and
          wherever such third-party notices normally appear. The contents
          of the NOTICE file are for informational purposes only and
          do not modify the License. You may add Your own attribution
          notices within Derivative Works that You distribute, alongside
          or as an addendum to the NOTICE text from the Work, provided
          that such additional attribution notices cannot be construed
          as modifying the License.

      You may add Your own copyright statement to Your modifications and
      may provide additional or different license terms and conditions
      for use, reproduction, or distribution of Your modifications, or
      for any such Derivative Works as a whole, provided Your use,
      reproduction, and distribution of the Work otherwise complies with
      the conditions stated in this License.

   5. Submission of Contributions. Unless You explicitly state otherwise,
      any Contribution intentionally submitted for inclusion in the Work
      by You to the Licensor shall be under the terms and conditions of
      this License, without any additional terms or conditions.
      Notwithstanding the above, nothing herein shall supersede or modify
      the terms of any separate license agreement you may have executed
      with Licensor regarding such Contributions.

   6. Trademarks. This License does not grant permission to use the trade
      names, trademarks, service marks, or product names of the Licensor,
      except as required for reasonable and customary use in describing the
      origin of the Work and reproducing the content of the NOTICE file.

   7. Disclaimer of Warranty. Unless required by applicable law or
      agreed to in writing, Licensor provides the Work (and each
      Contributor provides its Contributions) on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
      implied, including, without limitation, any warranties or conditions
      of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
      PARTICULAR PURPOSE. You are solely responsible for determining the
      appropriateness of using or redistributing the Work and assume any
      risks associated with Your exercise of permissions under this License.

   8. Limitation of Liability. In no event and under no legal theory,
      whether in tort (including negligence), contract, or otherwise,
      unless required by applicable law (such as deliberate and grossly
      negligent acts) or agreed to in writing, shall any Contributor be
      liable to You for damages, including any direct, indirect, special,
      incidental, or consequential damages of any character arising as a
      result of this License or out of the use or inability to use the
      Work (including but not limited to damages for loss of goodwill,
      work stoppage, computer failure or malfunction, or any and all
      other commercial damages or losses), even if such Contributor
      has been advised of the possibility of such damages.

   9. Accepting Warranty or Additional Liability. While redistributing
      the Work or Derivative Works thereof, You may choose to offer,
      and charge a fee for, acceptance of support, warranty, indemnity,
      or other liability obligations and/or rights consistent with this
      License. However, in accepting such obligations, You may act only
      on Your own behalf and on Your sole responsibility, not on behalf
      of any other Contributor, and only if You agree to indemnify,
      defend, and hold each Contributor harmless for any liability
      incurred by, or claims asserted against, such Contributor by reason
      of your accepting any such warranty or additional liability.

   END OF TERMS AND CONDITIONS
```
