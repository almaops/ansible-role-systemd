aboveops.systemd
=========

Wraps the systemd ansible module into the role

Description
-----------

This roles just wraps the systemd ansible module into the role.


Example
-------

    - role: aboveops.template
      template_content: |
        upstream grafana {
            {% for host in groups["monitoring"] %}
            server {{ hostvars[host].backnet_ip }}:3000;
            {% endfor %}
        }
      template_dest: "/etc/nginx/conf.d/grafana_upstream.conf"
    
    - role: aboveops.systemd
      systemd_service_name: nginx
      systemd_service_state: reloaded
      systemd_daemon_reload: false
      when: template_result is changed

Install
-------

This role can be installed from [Ansible Galaxy](https://galaxy.ansible.com/):

`ansible-galaxy install aboveops.systemd`

License
-------

MIT

Author Information
------------------

Dmitrii Kashin, <freehck@freehck.com>
