---
layout: post
title:  "C# prepared statement (SELECT, UPDATE) 간단하게"
categories: c#
---
```c#
        // 쿼리 접속
        MySqlConnection connection = new MySqlConnection("Server=localhost;Database=insa;Uid=root;Pwd=root;");

        public int logincheck(String id, String pw)
        {
            int check = 0;
            string selectQuery;
            selectQuery = "Select * from user where id=@id and pw=@pw";

            try
            {
                using (MySqlConnection conn = connection)
                {
                    conn.Open();
                    using (MySqlCommand cmd = new MySqlCommand(selectQuery, conn))
                    {
                        cmd.Parameters.AddWithValue("@id", id);
                        cmd.Parameters.AddWithValue("@pw", pw);
                        cmd.Prepare();

                        using (var reader = cmd.ExecuteReader())
                        {
                            while (reader.Read())
                            {
                                check = 1;
                            }
                        }
                    }
                    conn.Close();
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
            return check;
        }

        public void misscheck(String id)
        {
            try
            {
               
                connection.Open();
                int getresult = get_pwmiss(id, connection);
                MySqlCommand comm = new MySqlCommand();
                comm.Connection = connection;
                comm.CommandText = "UPDATE user SET password_miss=@password_miss where id=@id";
                comm.Parameters.AddWithValue("@id", id);
                comm.Parameters.AddWithValue("@password_miss", (getresult+1));
                comm.ExecuteNonQuery();
                connection.Close();
            }
            catch (Exception ex) {
                Console.WriteLine(ex);
            }

            
        }

        // 여기서 중복으로 커넥션해서 에러가 뜬거여서 자체적으로 커넥션하던가 따로 지금처럼 변수로 커넥션해야함.
        public int get_pwmiss(String id, MySqlConnection conn)
        {
            int miss = 0;
            string selectQuery = "Select password_miss from user where id=@id";
            try
            {
  

                    using (MySqlCommand cmd = new MySqlCommand(selectQuery, conn))
                    {
                        cmd.Parameters.AddWithValue("@id", id);
                        cmd.Prepare();

                        using (var reader = cmd.ExecuteReader())
                        {
                            while (reader.Read())
                            {
                                miss = int.Parse(reader.GetString(0));
                            
                            }
                            Console.WriteLine(miss);
                            if(reader != null) reader.Close();
                        }
                    }
          
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
            return miss;
        }
    }
```

using MySql.Data.MySqlClient로 하는 prepared statement