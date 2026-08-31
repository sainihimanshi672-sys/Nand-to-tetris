NOT--------
CHIP Not {
    IN in;
    OUT out;

    PARTS:
   Nand(a=in , b=in, out=out);
}

------AND---------

CHIP And {
    IN a, b;
    OUT out;
    
    PARTS:
    Nand(a=a , b=b , out=c );
    Nand(a=c , b=c , out=out );
}

------OR-------
CHIP Or {
    IN a, b;
    OUT out;

    PARTS:
    Not(in=a , out=c );
    Not(in=b , out=d );
    Nand(a=c , b=d , out=out );
}


------XOR--------
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    Or(a=a , b=b , out=orab );
    And(a=a, b=b , out=andab);
    Not(in=andab ,out=notand );
    And(a=orab , b=notand , out=out );
}


------MUX--------
CHIP Mux {
    IN a, b, sel;
    OUT out;

    PARTS:
    Not(in=sel, out=notSel);
    And(a=a, b=notSel, out=aOut);
    And(a=b, b=sel, out=bOut);
    Or(a=aOut, b=bOut, out=out);
}


--------DMUX-------
CHIP DMux {
    IN in, sel;
    OUT a, b;

    PARTS:

    Not(in=sel, out=notSel);
    And(a=in, b=notSel, out=a);
    And(a=in, b=sel, out=b);
}


-------NOT16--------
CHIP Not16 {
    IN in[16];
    OUT out[16];

      PARTS:
    Not(in=in[0], out=out[0]);
    Not(in=in[1], out=out[1]);
    Not(in=in[2], out=out[2]);
    Not(in=in[3], out=out[3]);
    Not(in=in[4], out=out[4]);
    Not(in=in[5], out=out[5]);
    Not(in=in[6], out=out[6]);
    Not(in=in[7], out=out[7]);
    Not(in=in[8], out=out[8]);
    Not(in=in[9], out=out[9]);
    Not(in=in[10], out=out[10]);
    Not(in=in[11], out=out[11]);
    Not(in=in[12], out=out[12]);
    Not(in=in[13], out=out[13]);
    Not(in=in[14], out=out[14]);
    Not(in=in[15], out=out[15]);
}