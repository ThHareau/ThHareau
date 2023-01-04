---
title: Stop worrying about PostgreSQL locks in your Rails migrations
period: 2020
link: https://medium.com/doctolib/stop-worrying-about-postgresql-locks-in-your-rails-migrations-3426027e9cc9
icon: fa-medium
---

Busy databases are tedious to migrate: Postgres locking mechanisms can rapidly bring the service down if migrations are not written carefully. In the following article, co-written with Romain Choquet, we explain how we are tackling that risk at Doctolib. 