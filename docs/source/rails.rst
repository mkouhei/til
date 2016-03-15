===============
 Ruby on Rails
===============

Admin User create
=================

Use "activeadmin" gem, prepare create_admin.rb script.

.. code-block:: ruby

   AdminUser.new(email: ARGV[0],
                 password: ARGV[1],
                 password_confirmation: ARGV[1])
   

.. code-block:: sh

   $ bundle exec rails runner create_admin.rb admin@example.com password

