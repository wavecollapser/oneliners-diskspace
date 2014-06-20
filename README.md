oneliners-diskspace
===================

Oneliner for crontab -e to mail diskspace probs out to sysadm group, every server needs this!


MAILTO=sysadm-group@domain.com
#
# MONITORING
#
# Diskspace and mail out to sysadm group, at 85%+ usage
#
00 */3 * * * df -Pl|sed -rn -e "s/^([-a-zA-Z0-9_/.:]+).* ([0-9.,]+)\%.* ([a-zA-Z0-9_/]+)\$/\3\t\1\t\2\%/g" -e "s/(8[5-9.,]+\%|9[0-9.,]+\%|1[0-9.,]{2,}\%)$/\1/gp;d" 



there you go, put in crontab -e :-)


root@ns1:~# df -Pl|sed -rn -e "s/^([-a-zA-Z0-9_/.:]+).* ([0-9.,]+)\%.* ([a-zA-Z0-9_/]+)\$/\3\t\1\t\2\%/g" -e "s/(8[5-9.,]+\%|9[0-9.,]+\%|1[0-9.,]{2,}\%)$/\1/gp;d"
/               /dev/vda1       89%
/wwwroot        /dev/vdb1       93%

neat format output + mailing... all in a oneliner with sed, one tool to rule them all :)
