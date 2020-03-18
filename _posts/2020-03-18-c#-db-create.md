---
title: "C# 데이터베이스 간단하게 연결 및 조회"
categories: c#
---

using MySql.Data.MySqlClient;
namespace project
{
    class database
    {
        // 쿼리 접속
        MySqlConnection connection = new MySqlConnection("Server=localhost;Database=insa;Uid=root;Pwd=root;");
        // 쿼리 연결
        public void connectionDB()
        {
            connection.Open();
        }
        public int logincheck(String id, String pw)
        {
            int check = 0;
            if(id.Equals("") && pw.Equals(""))
            {
                check = 0;
            }
            try //예외 처리
            {
                string sql = "SELECT * FROM user where id='"+id+"' and pw='"+pw+"'";
                //ExecuteReader를 이용하여
                //연결 모드로 데이타 가져오기
                MySqlCommand cmd = new MySqlCommand(sql, connection);
                MySqlDataReader table = cmd.ExecuteReader();
                if (table.Read())
                {
                    Console.WriteLine("login success");
                    check = 1;
                }
                table.Close();
            }
            catch (Exception ex)
            {
                Console.WriteLine("실패");
                Console.WriteLine(ex.ToString());
            }
            return check;
        }
    }
}


쿼리접속부분에서 아이디, 비밀번호, DB입력을 해주면됨
접속 후에 SELECT문을 이용하여 데이터값이 있는지 체크


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
