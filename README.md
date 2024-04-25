RT-Thread Vision Board with RASmartConfiguration
===

the repository show "How to use RASmartConfiguration with cmake/ninja and arm gcc toolchain"
and use pyocd to flash device

the below show all operation steps and result
---

```
kunyi@kunyi-TP-P53:/tmp/RASmartConfigurator/RTT_VisonBoard$ mkdir build
kunyi@kunyi-TP-P53:/tmp/RASmartConfigurator/RTT_VisonBoard$ cd build/
kunyi@kunyi-TP-P53:/tmp/RASmartConfigurator/RTT_VisonBoard/build$ cmake .. -GNinja -DCMAKE_FIND_ROOT_PATH=/home/kunyi/renesas/ra/e2studio_v2024-01.1_fsp_v5.2.0/toolchains/gcc_arm/arm-gnu-toolchain-13.2.Rel1-x86_64-arm-none-eabi/bin -DCMAKE_TOOLCHAIN_FILE=../cmake/gcc.cmake
-- The ASM compiler identification is GNU
-- Found assembler: /home/kunyi/renesas/ra/e2studio_v2024-01.1_fsp_v5.2.0/toolchains/gcc_arm/arm-gnu-toolchain-13.2.Rel1-x86_64-arm-none-eabi/bin/arm-none-eabi-gcc
-- Configuring done
-- Generating done
-- Build files have been written to: /tmp/RASmartConfigurator/RTT_VisonBoard/build
kunyi@kunyi-TP-P53:/tmp/RASmartConfigurator/RTT_VisonBoard/build$ ninja
[22/23] Linking C executable RTT_VisonBoard.elf
Running RASC post-build to generate Smart Bundle ( .sbd ) file
Apr 25, 2024 12:44:13 PM org.apache.aries.spifly.BaseActivator log
INFO: Registered provider org.slf4j.simple.SimpleServiceProvider of service org.slf4j.spi.SLF4JServiceProvider in bundle slf4j.simple
100% Generating Smart Bundle
[23/23] Creating S-record file in /tmp/RASmartConfigurator/RTT_VisonBoard/build
kunyi@kunyi-TP-P53:/tmp/RASmartConfigurator/RTT_VisonBoard/build$ pyocd load --target=r7fa8d1bh RTT_VisonBoard.elf
0001586 I Loading /tmp/RASmartConfigurator/RTT_VisonBoard/build/RTT_VisonBoard.elf [load_cmd]
0001590 W Failed to add data chunk: no memory region defined for address 0x27030080 [file_programmer]
[==================================================] 100%
0003099 I Erased 0 bytes (0 sectors), programmed 0 bytes (0 pages), skipped 5632 bytes (58 pages) at 3.65 kB/s [loader]
```
