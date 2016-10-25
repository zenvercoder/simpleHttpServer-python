### Some great tutorials

* http://docs.python-guide.org/en/latest/starting/install/osx/

* https://pythonspot.com/en/flask-web-app-with-python/

* https://pythonspot.com/en/python-database-postgresql/

* for virtual environment virtualenv venv

* `mysql -uroot -p`

mysql>

CREATE DATABASE Flask;

CREATE TABLE `Flask`.`tbl_user` (
  `user_id` BIGINT UNIQUE AUTO_INCREMENT,
  `user_name` VARCHAR(45) UNIQUE,
  `user_username` VARCHAR(45) UNIQUE,
  `user_password` VARCHAR(45) UNIQUE,
  PRIMARY KEY (`user_id`));

  DELIMITER $$

  USE Flask$$

  CREATE DEFINER=`root`@`localhost` PROCEDURE `sp_createUser`(
      IN p_name VARCHAR(20),
      IN p_username VARCHAR(20),
      IN p_password VARCHAR(20)
  )
  BEGIN
      if ( select exists (select 1 from tbl_user where user_username = p_username) ) THEN

          select 'Username Exists !!';

      ELSE

          insert into tbl_user
          (
              user_name,
              user_username,
              user_password
          )
          values
          (
              p_name,
              p_username,
              p_password
          );

      END IF;
  END$$
  DELIMITER ;
