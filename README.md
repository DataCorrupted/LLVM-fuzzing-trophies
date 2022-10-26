# LLVM-fuzzing-trophies

- &#x2714;: Compiled successfully.
- &#x23F3;: Compiler timed out, possibly infinite recursion
- &#x274C;: Compiler crashed due to a bug or assertion
- &#x1F6A7;: Compiler crashed due to missing features
- &#x26A0;: Compiler didn't crash, but misbehaved	

| Issue #                                                    | Description                                                                                              |                                    Fixing commit                                    | Upstream  |  LLVM 15  |  LLVM 14  |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------: | :-------: | :-------: | :-------: |
| LLVM                                                       |                                                                                                          |                                                                                     |           |           |           |
| [57251](https://github.com/llvm/llvm-project/issues/57251) | `DAGTypeLegalizer::RemapId` infinite recursion on AArch64, X86, and AIE.                                 |                                          -                                          | &#x23F3;  | &#x23F3;  | &#x23F3;  |
| [57452](https://github.com/llvm/llvm-project/issues/57452) | Codegen SExt index value of `extractelement`, translating `i1 true` into `i32 -1`.                       | [c2e7c9cb33ac](https://reviews.llvm.org/rGc2e7c9cb33acbd118fe5011a1607d6cf8e21de34) | &#x2714;  | &#x274C;  | &#x274C;  |
| [57658](https://github.com/llvm/llvm-project/issues/57658) | Infinite recursion in `VectorLegalizer::LegalizeOp`.                                                     | [545affbf79bf](https://reviews.llvm.org/rG545affbf79bfbc19659a0f442f22558791aa4404) | &#x2714;  | &#x23F3;  | &#x23F3;  |
| [58511](https://github.com/llvm/llvm-project/issues/58511) | Infinite recursion in `foldBinOpIntoSelect`.                                                             | [00816714f965](https://reviews.llvm.org/rG00816714f96505c59c236f3f0fd2eb815c57f674) | &#x2714;  | &#x23F3;  | &#x23F3;  |
| [58538](https://github.com/llvm/llvm-project/issues/58538) | `CodeGenPrepare` infinitely sinking `cmp`.                                                               |                                          -                                          | &#x23F3;  | &#x23F3;  | &#x23F3;  |
| [58583](https://github.com/llvm/llvm-project/issues/58583) | IR Verifier didn't check if switch case is constant                                                      |                                          -                                          | &#x26A0;  | &#x26A0;  | &#x26A0;  |
| [58580](https://github.com/llvm/llvm-project/issues/58580) | SimplifyCFG  infinite recursion assertion failed                                                         |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| AArch64                                                    |                                                                                                          |                                                                                     |           |           |           |
| [57282](https://github.com/llvm/llvm-project/issues/57282) | Double free given invalid index in `insertelement`                                                       | [3dd861818a68](https://reviews.llvm.org/rG3dd861818a68b2e0b21d426ee956ec8d69f89c88) | &#x2714;  | &#x274C;  | &#x274C;  |
| [57326](https://github.com/llvm/llvm-project/issues/57326) | SelectionDAG uses uninitialized array and have OOB Write given long `shuffelvector` mask.                | [2343ad755d60](https://reviews.llvm.org/rG2343ad755d602fe67e3418d4edf0a5d0780045d6) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58050](https://github.com/llvm/llvm-project/issues/58050) | `fcmp true / false` used in `and` / `or` branching condition causes crash `Unknown FP condition!`        |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58156](https://github.com/llvm/llvm-project/issues/58156) | GlobalIsel unable to legalize vectorized binaryop(`G_ADD`, `G_SUB`, ...)                                 |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58211](https://github.com/llvm/llvm-project/issues/58211) | GlobalIsel unable to translate `ret` with `v1i8 / v1i16`                                                 |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58274](https://github.com/llvm/llvm-project/issues/58274) | GlobalIsel cannot select `G_ZEXT` / `G_SEXT` / `G_ANYEXT` with `v2i16`                                   |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58350](https://github.com/llvm/llvm-project/issues/58350) | Storing a `v1f32` along with a `f32` causes assertion error "Extract subvector index must be a constant" | [c1909d73372e](https://reviews.llvm.org/rGc1909d73372e669a44a2aefe82de873c2161cc44) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58615](https://github.com/llvm/llvm-project/issues/58615) | Passing a v1f32 arg through memory crashes backend with "Invalid TRUNCATE!" assertion error              |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| AMDGPU                                                     |                                                                                                          |                                                                                     |           |           |           |
| [57406](https://github.com/llvm/llvm-project/issues/57406) | GlobalIsel `AMDGPUPreLegalizerCombiner` double frees on negative index.                                  | [8901f7cebc73](https://reviews.llvm.org/rG8901f7cebc73383d0cda19a870ffe410a67653e9) | &#x2714;  | &#x274C;  | &#x274C;  |
| [57408](https://github.com/llvm/llvm-project/issues/57408) | GlobalIsel `legalizeExtractVectorElt` crashes on negative index.                                         | [8901f7cebc73](https://reviews.llvm.org/rG8901f7cebc73383d0cda19a870ffe410a67653e9) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58331](https://github.com/llvm/llvm-project/issues/58331) | `mul` `v1i8` / `v1i16` causes crash during IR optimizations due to type mismatch                         | [838fd611b79e](https://reviews.llvm.org/rG838fd611b79e3514eead5dd724140df046172ef1) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58210](https://github.com/llvm/llvm-project/issues/58210) | No registers from class available to allocate for R600 / Cannot select for AMDGCN                        |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58171](https://github.com/llvm/llvm-project/issues/58171) | Allocating large mumber of `bool`s on stack causes "Register number out of range"                        |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| NVPTX                                                      |                                                                                                          |                                                                                     |           |           |           |
| [57398](https://github.com/llvm/llvm-project/issues/57398) | SelectionDAG Cannot select `dynamic_stackalloc`                                                          |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [57404](https://github.com/llvm/llvm-project/issues/57404) | SelectionDAG Cannot select `mul i1`                                                                      |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [57405](https://github.com/llvm/llvm-project/issues/57405) | SelectionDAG Cannot select `setcc`                                                                       |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58305](https://github.com/llvm/llvm-project/issues/58305) | Assertion `CastInst::castIsValid(opc, C, Ty) && "Invalid constantexpr cast!"` failed                     |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58428](https://github.com/llvm/llvm-project/issues/58428) | `icmp i1` used as branching condition crashes backend                                                    |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| RISCV                                                      |                                                                                                          |                                                                                     |           |           |           |
| [58025](https://github.com/llvm/llvm-project/issues/58025) | Copying a `v1f32` vector between blocks causes assertion error "Invalid `ANY_EXTEND`"                    | [12357e88af66](https://reviews.llvm.org/rG12357e88af669b00a5c4c607b93b716a6c474846) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58027](https://github.com/llvm/llvm-project/issues/58027) | Cannot scavenge register without an emergency spill slot                                                 |                                                                                     | &#x274C;  | &#x274C;  | &#x274C;  |
| X86                                                        |                                                                                                          |                                                                                     |           |           |           |
| [57283](https://github.com/llvm/llvm-project/issues/57283) | SelectionDAG assertion failure on shift                                                                  | [5377abcde240](https://reviews.llvm.org/rG5377abcde2409dc066b4b9e3425900df1eff927e) | &#x2714;  | &#x2714;  | &#x274C;  |
| [57474](https://github.com/llvm/llvm-project/issues/57474) | SelectionDAG assertion failure on shift                                                                  | [eaede4b5b7cf](https://reviews.llvm.org/rGeaede4b5b7cfc13ca0e484b4cb25b2f751d86fd9) | &#x2714;  | &#x2714;  | &#x274C;  |
| [58455](https://github.com/llvm/llvm-project/issues/58455) | Assertion "Can't handle this yet!" failed when scheduling                                                |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |

