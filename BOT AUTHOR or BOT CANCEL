# -*- coding: utf-8 -*-
import LINETHB
from LINETHB.lib.curve.ttypes import *
from datetime import datetime
import time,random,sys,json,codecs,threading,glob,os,subprocess,multiprocessing

cl = LINETHB.LINE()
try:
    cl.login(qr=True)
    print u"login success"
except:
    pass

reload(sys)
sys.setdefaultencoding('utf-8')


mid = cl.getProfile().mid
def cancel(op):
    try:
        SD=op.param1
        if op.type == 0:
            return
        if op.type == 13:
            if mid in op.param3:
                try:
                    cl.acceptGroupInvitation(SD)
                    group = cl.getGroup(SD)
                    if group.invitee is not None:
                        gInviMids = [contact.mid for contact in group.invitee]
                        cl.cancelGroupInvitation(SD, gInviMids)

                        cl.sendText(SD,"DONE BRO􀜁􀅹Salute􏿿􀜁􀅹Salute􏿿。")
                    else:
                        cl.sendText(SD,"NO INVITAN BRO􀜁􀅇Forever Alone􏿿􀜁􀅇Forever Alone􏿿。")
                    cl.leaveGroup(SD)
                except:
                    pass
            else:
                pass

    except Exception as error:
        #print error
        pass


while True:
    try:
        Ops = cl.fetchOps(cl.Poll.rev, True)
    except EOFError:
        raise Exception("It might be wrong revision\n" + str(cl.Poll.rev))

    for Op in Ops:
        if (Op.type != OpType.END_OF_OPERATION):
            cl.Poll.rev = max(cl.Poll.rev, Op.revision)
            bot(Op)
