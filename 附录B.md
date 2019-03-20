这是ASM中所有的常量操作数，在ASM中用其指代JVM指令，可以用ACC_PUBLIC这样更有可读性的名字代替，也可以用数字表示


public interface Opcodes {

    // ASM的版本，以下表述均合法

    int ASM4 = 4 << 16 | 0 << 8 | 0; 
    int ASM5 = 5 << 16 | 0 << 8 | 0;

    // Java版本，需要限定Java版本时使用，至于为什么是45-52不得而知

    int V1_1 = 3 << 16 | 45;
    int V1_2 = 0 << 16 | 46;
    int V1_3 = 0 << 16 | 47;
    int V1_4 = 0 << 16 | 48;
    int V1_5 = 0 << 16 | 49;
    int V1_6 = 0 << 16 | 50;
    int V1_7 = 0 << 16 | 51;
    int V1_8 = 0 << 16 | 52;

    // 所有的访问修饰关键字，例如public，private之类

    int ACC_PUBLIC = 0x0001; // class, field, method
    int ACC_PRIVATE = 0x0002; // class, field, method
    int ACC_PROTECTED = 0x0004; // class, field, method
    int ACC_STATIC = 0x0008; // field, method
    int ACC_FINAL = 0x0010; // class, field, method, parameter
    int ACC_SUPER = 0x0020; // class
    int ACC_SYNCHRONIZED = 0x0020; // method
    int ACC_VOLATILE = 0x0040; // field
    int ACC_BRIDGE = 0x0040; // method
    int ACC_VARARGS = 0x0080; // method
    int ACC_TRANSIENT = 0x0080; // field
    int ACC_NATIVE = 0x0100; // method
    int ACC_INTERFACE = 0x0200; // class
    int ACC_ABSTRACT = 0x0400; // class, method
    int ACC_STRICT = 0x0800; // method
    int ACC_SYNTHETIC = 0x1000; // class, field, method, parameter
    int ACC_ANNOTATION = 0x2000; // class
    int ACC_ENUM = 0x4000; // class(?) field inner
    int ACC_MANDATED = 0x8000; // parameter
    int ACC_DEPRECATED = 0x20000; // class, field, method //ACC_DEPRECATED代指@Deprecated注解标注的类或字段，方法

    //基本类型

    int T_BOOLEAN = 4;
    int T_CHAR = 5;
    int T_FLOAT = 6;
    int T_DOUBLE = 7;
    int T_BYTE = 8;
    int T_SHORT = 9;
    int T_INT = 10;
    int T_LONG = 11;

    // tags for Handle

    int H_GETFIELD = 1;  //获取字段
    int H_GETSTATIC = 2; //获取静态变量
    int H_PUTFIELD = 3;  //指定字段
    int H_PUTSTATIC = 4; //指定静态变量
    int H_INVOKEVIRTUAL = 5;  //调用对象实例方法
    int H_INVOKESTATIC = 6; //调用静态方法
    int H_INVOKESPECIAL = 7;//调用实例初始化方法（<init>方法），private或父类方法
    int H_NEWINVOKESPECIAL = 8; 
    int H_INVOKEINTERFACE = 9;//调用接口方法

    // stack map frame types
    //每调用一次方法，便会为其开辟栈空间，生成栈帧，以下都是栈帧相关操作

    /**
     * Represents an expanded frame. See {@link ClassReader#EXPAND_FRAMES}.
     */
    int F_NEW = -1;

    /**
     * Represents a compressed frame with complete frame data.
     */
    int F_FULL = 0;

    /**
     * Represents a compressed frame where locals are the same as the locals in
     * the previous frame, except that additional 1-3 locals are defined, and
     * with an empty stack.
     */
    int F_APPEND = 1;

    /**
     * Represents a compressed frame where locals are the same as the locals in
     * the previous frame, except that the last 1-3 locals are absent and with
     * an empty stack.
     */
    int F_CHOP = 2;

    /**
     * Represents a compressed frame with exactly the same locals as the
     * previous frame and with an empty stack.
     */
    int F_SAME = 3;

    /**
     * Represents a compressed frame with exactly the same locals as the
     * previous frame and with a single value on the stack.
     */
    int F_SAME1 = 4;
    

    //以下都是JVM指令，将常量名小写就是其对应的JVM指令，例如ACONST_NULL小写就是aconst_null指令
    //1，2，3，4，5等对应的也是真实的JVM操作码，186对应ba
    //Insn是instruction的缩写，可以深入到方法内部去修改其变量和操作
    //CONST指常量，I指int，F指float，D指double，C指char，S指short，L指long，B指byte
    //ADD，MIN，MUL，DIV指加减乘除，IADD就是两个int相加    
    //AND，OR，XOR指按位与，按位或，按位或非
    //2指的是to，例如I2B指int to byte
    //LOAD指入栈，STORE指出栈，ALOAD指任意局部变量入栈
    //RETURN指返回

    int NOP = 0; // visitInsn
    int ACONST_NULL = 1; // -将一个空引用推到栈顶
    int ICONST_M1 = 2; // -将-1加载到栈顶
    int ICONST_0 = 3; // -将0加载到栈顶
    int ICONST_1 = 4; // -将1加载到栈顶
    int ICONST_2 = 5; // -将2加载到栈顶
    int ICONST_3 = 6; // -将3加载到栈顶
    int ICONST_4 = 7; // -将4加载到栈顶
    int ICONST_5 = 8; // -将5加载到栈顶（以上都是int）
    int LCONST_0 = 9; // -将0L加载到栈顶
    int LCONST_1 = 10; // -将1L加载到栈顶
    int FCONST_0 = 11; // -将0F加载到栈顶
    int FCONST_1 = 12; // -将1F加载到栈顶
    int FCONST_2 = 13; // -将2F加载到栈顶
    int DCONST_0 = 14; // -将0D加载到栈顶
    int DCONST_1 = 15; // -将1D加载到栈顶
    int BIPUSH = 16; // visitIntInsn -将byte值作为int推到栈顶
    int SIPUSH = 17; // -将short作为int推到栈顶
    int LDC = 18; // visitLdcInsn -从常量池 (可以是String, int, float, Class, java.lang.invoke.MethodType, or java.lang.invoke.MethodHandle)     中将一个#index常量推到栈顶
    int ILOAD = 21; // visitVarInsn //从局部变量表中加载int值到栈顶
    int LLOAD = 22; // -从局部变量表加载long到栈顶
    int FLOAD = 23; // -从局部变量表加载float到栈顶
    int DLOAD = 24; // -从局部变量表加载double到栈顶
    int ALOAD = 25; // -从局部变量表加载Object引用到栈顶
    int IALOAD = 46; // visitInsn -从数组加载int到栈顶
    int LALOAD = 47; // -从数组加载long到栈顶
    int FALOAD = 48; // -从数组加载float到栈顶
    int DALOAD = 49; // -从数组加载double到栈顶
    int AALOAD = 50; // -从数组加载Object引用到栈顶
    int BALOAD = 51; // -从数组加载boolean值到栈顶
    int CALOAD = 52; // -从数组加载char值到栈顶
    int SALOAD = 53; // -从数组加载short到栈顶
    int ISTORE = 54; // visitVarInsn 将int值保存到局部变量表
    int LSTORE = 55; // -将long值保存到局部变量表
    int FSTORE = 56; // -将float值保存到局部变量表
    int DSTORE = 57; // -将double值保存到局部变量表
    int ASTORE = 58; // -将Object引用保存到局部变量表
    int IASTORE = 79; // visitInsn -将int值保存到数组中
    int LASTORE = 80; // -将long值保存到数组中
    int FASTORE = 81; // -将float值保存到数组中
    int DASTORE = 82; // -将double值保存到数组中
    int AASTORE = 83; // -将Object引用保存到数组中
    int BASTORE = 84; // -将boolean值保存到数组中
    int CASTORE = 85; // -将char值保存到数组中
    int SASTORE = 86; // -将short值保存到数组中
    int POP = 87; // -丢弃栈顶元素
    int POP2 = 88; // -丢弃栈顶的两个元素（如果是double或long就只有一个）
    int DUP = 89; // -复制栈顶元素
    int DUP_X1 = 90; // -复制栈顶元素，并将其插入栈顶的两个元素下面，形如value2, value1 → value1, value2, value1 
    int DUP_X2 = 91; // -复制栈顶元素，并将其插入栈顶的三个元素（前提是value2不能是double或long）或两个元素（这时value2是long或double，或占了value
    3的位置，形如value3, value2, value1 → value1, value3, value2, value1 
    int DUP2 = 92; // -复制栈顶的两个元素
    int DUP2_X1 = 93; // -形如value3, {value2, value1} → {value2, value1}, value3, {value2, value1} 
    int DUP2_X2 = 94; // -形如{value4, value3}, {value2, value1} → {value2, value1}, {value4, value3}, {value2, value1} 
    int SWAP = 95; // -交换栈顶的两个值，注意两个值不能是double或long
    int IADD = 96; // -
    int LADD = 97; // -
    int FADD = 98; // -
    int DADD = 99; // -
    int ISUB = 100; // -
    int LSUB = 101; // -
    int FSUB = 102; // -
    int DSUB = 103; // -
    int IMUL = 104; // -
    int LMUL = 105; // -
    int FMUL = 106; // -
    int DMUL = 107; // -
    int IDIV = 108; // -
    int LDIV = 109; // -
    int FDIV = 110; // -
    int DDIV = 111; // -
    int IREM = 112; // -
    int LREM = 113; // -
    int FREM = 114; // -
    int DREM = 115; // -
    int INEG = 116; // -
    int LNEG = 117; // -
    int FNEG = 118; // -
    int DNEG = 119; // -
    int ISHL = 120; // -
    int LSHL = 121; // -
    int ISHR = 122; // -
    int LSHR = 123; // -
    int IUSHR = 124; // -
    int LUSHR = 125; // -
    int IAND = 126; // -
    int LAND = 127; // -
    int IOR = 128; // -
    int LOR = 129; // -
    int IXOR = 130; // -
    int LXOR = 131; // -
    int IINC = 132; // visitIincInsn
    int I2L = 133; // visitInsn，将int转为long，以下类推
    int I2F = 134; // -
    int I2D = 135; // -
    int L2I = 136; // -
    int L2F = 137; // -
    int L2D = 138; // -
    int F2I = 139; // -
    int F2L = 140; // -
    int F2D = 141; // -
    int D2I = 142; // -
    int D2L = 143; // -
    int D2F = 144; // -
    int I2B = 145; // -
    int I2C = 146; // -
    int I2S = 147; // -
    int LCMP = 148; // -比较大小，如果value1>value2将1推到栈顶，相等则是0，反之则为-1
    int FCMPL = 149; // -比较两个float，下同
    int FCMPG = 150; // -
    int DCMPL = 151; // -比较两个double，下同
    int DCMPG = 152; // -
    int IFEQ = 153; // visitJumpInsn，当栈顶int型数值等于0时跳转
    int IFNE = 154; // -当栈顶int型数值不等于0时跳转
    int IFLT = 155; // -当栈顶int型数值小于0时跳转
    int IFGE = 156; // -当栈顶int型数值大于等于0时跳转
    int IFGT = 157; // -当栈顶int型数值大于0时跳转
    int IFLE = 158; // -当栈顶int型数值小于等于0时跳转
    int IF_ICMPEQ = 159; // -比较栈顶两int型数值大小，当结果等于0时跳转
    int IF_ICMPNE = 160; // -比较栈顶两int型数值大小，当结果不等于0时跳转
    int IF_ICMPLT = 161; // -比较栈顶两int型数值大小，当结果小于0时跳转
    int IF_ICMPGE = 162; // -比较栈顶两int型数值大小，当结果大于等于0时跳转
    int IF_ICMPGT = 163; // -比较栈顶两int型数值大小，当结果大于0时跳转
    int IF_ICMPLE = 164; // -比较栈顶两int型数值大小，当结果小于等于0时跳转
    int IF_ACMPEQ = 165; // -比较栈顶两Object引用，当结果相等时跳转
    int IF_ACMPNE = 166; // -比较栈顶两Object引用，当结果不相等时跳转
    int GOTO = 167; //-跳转
    int JSR = 168; // -跳转至指定16位栈偏移位置，并将jsr下一条指令地址压入栈顶
    int RET = 169; // visitVarInsn，返回至本地变量指定的#index的指令位置（一般与jsr, jsr_w联合使用）
    int TABLESWITCH = 170; // visiTableSwitchInsn，用于switch条件跳转，case值连续（可变长度指令）
    int LOOKUPSWITCH = 171; // visitLookupSwitch，用于switch条件跳转，case值不连续（可变长度指令）
    int IRETURN = 172; // visitInsn
    int LRETURN = 173; // -
    int FRETURN = 174; // -
    int DRETURN = 175; // -
    int ARETURN = 176; // -
    int RETURN = 177; // -返回void
    int GETSTATIC = 178; // visitFieldInsn，获取指定类的静态字段，并将其值推到栈顶
    int PUTSTATIC = 179; // -为指定类的静态字段赋值
    int GETFIELD = 180; // -获取指定类的实例字段，并将其值推到栈顶
    int PUTFIELD = 181; // -为指定的类的实例字段赋值
    int INVOKEVIRTUAL = 182; // visitMethodInsn，调用实例方法（Java中所有的方法都是可以直接覆写的虚方法，所以叫virtual）
    int INVOKESPECIAL = 183; // -调用超类构造方法，实例初始化方法，私有方法
    int INVOKESTATIC = 184; // -调用静态方法
    int INVOKEINTERFACE = 185; // -调用接口方法
    int INVOKEDYNAMIC = 186; // visitInvokeDynamicInsn 调用动态方法
    int NEW = 187; // visitTypeInsn 创建对象
    int NEWARRAY = 188; // visitIntInsn 创建基本类型数组
    int ANEWARRAY = 189; // visitTypeInsn 创建对象数组
    int ARRAYLENGTH = 190; // visitInsn 将数组长度推入栈顶
    int ATHROW = 191; // -将栈顶的异常抛出
    int CHECKCAST = 192; // visitTypeInsn 检验类型转换，检验未通过将抛出ClassCastException
    int INSTANCEOF = 193; // -检验对象是否是指定的类的实例，如果是将1推入栈顶，否则将0推入栈顶
    int MONITORENTER = 194; // visitInsn 获得对象的锁
    int MONITOREXIT = 195; // -释放对象锁
    int MULTIANEWARRAY = 197; // visitMultiANewArrayInsn
    int IFNULL = 198; // visitJumpInsn 如果栈顶元素null时跳转
    int IFNONNULL = 199; // -栈顶元素不为null时跳转
}

