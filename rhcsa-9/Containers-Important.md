# Attach persistant storage to podman container
1. ``sudo useradd rambo ; sudo passwd rambo``
2. ``sudo mkdir /testdir``
3. ``sudo chmod o+w /testdir``
4. ``sudo chown $user:$user /testdir``
5. ``sudo semanage fcontext -a -t container_file_t "/testdir(/.*?)"``
6. ``podman run -d --name myweb -v /testdir:/var/lib/mysql:Z -p 8089:80 nginx``
7. ``podman exec myweb ls /var/lib/mysql``

# Create systemd service from podman container
1. ``loginctl enable-linger rambo``
2. ``loginctl show-user rambo``
3. ``mkdir ~/.config/systemd/user; cd ~/.config/systemd/user``
4. ``podman generate systemd --name myweb --files --new``
5. ``systemctl --user daemon-reload``
6. ``systemctl --user enable container-webmaster.service``
7. ``systemctl --user status container-webmaster.service``
8. ``curl localhost:8089``
