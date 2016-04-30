# cmake


EXEC_PROGRAM
EXEC_PROGRAM(Executable [dir where to run] [ARGS <args>][OUTPUT_VARIABLE <var>] [RETURN_VALUE <value>])
用于在指定目录运行某个程序（默认为当前CMakeLists.txt所在目录）,通过ARGS添加参数,通过OUTPUT_VARIABLE和RETURN_VALUE获取输出和返回值,如下示例

# 在src中运行ls命令,在src/CMakeLists.txt添加
EXEC_PROGRAM(ls ARGS "*.c" OUTPUT_VARIABLE LS_OUTPUT RETURN_VALUE LS_RVALUE)
IF (not LS_RVALUE)
    MESSAGE(STATUS "ls result: " ${LS_OUTPUT}) # 缩进仅为美观,语法无要求
ENDIF(not LS_RVALUE)