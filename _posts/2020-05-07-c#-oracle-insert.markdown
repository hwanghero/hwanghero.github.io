---
layout: post
title: "C# oracle prepared-statement (INSERT)"
categories: c#
---

```c#
        public int thrm_forl_add(String forl_empno, String forl_code, String forl_score, String forl_acqdate, String forl_organ, String datasys1, String datasys2, String datasys3)
        {
            int check = 1;
            try
            {
                if (GetConnection() == true)
                {
                    OracleCommand comm = new OracleCommand();
                    comm.Connection = Connection;
                    comm.CommandText = @"INSERT INTO THRM_FORL_HWY values(:empno, :resno, :name, :cname, :ename, :edu_dept, :edu_degree, :edu_grade, :edu_gra, :datasys1, :datasys2, :datasys3)";
                    comm.Parameters.Add("empno", forl_empno);
                    comm.Parameters.Add("resno", forl_code);
                    comm.Parameters.Add("name", forl_score);
                    comm.Parameters.Add("cname", forl_acqdate);
                    comm.Parameters.Add("ename", forl_organ);
                    comm.Parameters.Add("datasys1", datasys1);
                    comm.Parameters.Add("datasys2", datasys2);
                    comm.Parameters.Add("datasys3", datasys3);
                    comm.Prepare();
                    comm.ExecuteNonQuery();
                    comm.Cancel();
                    comm.Dispose();
                    check = 0;
                }
            }
            catch (Exception ex)
            {
                check = 1;
                Console.WriteLine(ex);
            }
            return check;
        }
```