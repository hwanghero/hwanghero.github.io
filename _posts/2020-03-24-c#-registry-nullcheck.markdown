---
layout: post
title:  "C# 레지스트리(registry) 생성/불러오기/null체크"
categories: c#
---
```c#
        RegistryKey reg;

        // 아이디 레지스트리 생성
        public void Set_ID_Registry(string id)
        {
            //키 생성하기
            reg = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("insa-management");
            reg.SetValue("regID", id);
            reg.Close();
        }

        // 체크 레지스트리 생성
        public void Set_Savecheck_Registry(Boolean savecheck)
        {
            //키 생성하기
            reg = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("insa-management");
            reg.SetValue("regSave", savecheck);
            reg.Close();
        }

        // 아이디 값 불러오기
        public String Get_ID_Registry()
        {
            String save_reg = "";
            if (reg != null)
            {
                reg = Microsoft.Win32.Registry.CurrentUser;
                reg = reg.OpenSubKey("insa-management", true);
                save_reg = reg.GetValue("regID", "").ToString();
            }
            return save_reg;
        }

        // 체크 값 불러오기
        public String Get_Save_Registry()
        {
            String save_reg = "";

            reg = Microsoft.Win32.Registry.CurrentUser;
            reg = reg.OpenSubKey("insa-management", true);
            if(reg != null)
            {
                save_reg = reg.GetValue("regSave", "").ToString();
            }
            return save_reg;
        }
```