# Compose Bookshelf

This repository is collection of Docker Compose configurations for self-hosters who want to deploy their own services quickly and easily. Each folder contains a ready-to-use Docker Compose file along with necessary configuration files.

Feel free to explore the different services and deploy them on your own infrastructure!

> [!NOTE]
> If you do not know where to start with the hardware, have a look at this other project of mine! [MyHomeNAS](https://github.com/MorganKryze/MyHomeNAS)

## Available Services

### Security & privacy

- [ ] SearXNG - Privacy-respecting metasearch engine.
- [ ] Vaultwarden - Self-hosted password manager.
- [ ] Enclosed - Secure pastebin and tiny file sharing service.

### Finances

- [ ] MaybeOS - Personal finance and budgeting tool.
- [ ] Wapy.dev - Subsciption tracker and bill reminder service.

### Online editors

- [ ] Excalidraw - Virtual whiteboard for sketching and diagramming.
- [ ] Drawio - Diagramming tool for creating flowcharts and diagrams.
- [ ] Etherpad - Collaborative real-time text editor.
- [ ] Docmost - Collaborative markdown editor with live preview.

### Files

- [ ] FileBrowser - Web-based file manager for browsing and managing files.
- [ ] Erugo - Simple file hosting and sharing service.
- [ ] Immich - Image and video backup solution with web interface.
- [ ] Kiwix - Offline reader for web content like Wikipedia.

### Media

- [ ] Jellyfin - Media server for streaming your personal media collection.
- [ ] Jellyseerr - Media request and management tool for Jellyfin.
- [ ] JellyStat - Statistics and analytics for your Jellyfin server.
- [x] [Wizarr](https://github.com/MorganKryze/compose-bookshelf/blob/main/services/media/wizarr/compose.yml) - Invitations and user management for Jellyfin.
- [x] [Calibre-Web](https://github.com/MorganKryze/compose-bookshelf/blob/main/services/media/calibre/compose.yml) - Web-based interface for managing your eBook collection.

### Media conversion

- [ ] StirlingPDF - PDF conversion and manipulation service.
- [ ] ConvertX - General file conversion service for images and videos.
- [ ] Omnitools - A suite of media conversion and processing tools.
- [ ] Mazanoke - Picture file conversion and management service.

### Monitoring

- [ ] Uptime Kuma - Self-hosted monitoring tool for websites and services.

### Miscellaneous

- [ ] OpenSpeedTest - Self-hosted internet speed test service.
- [ ] LinkStack - Home to all your important links and contacts.
- [ ] Kutt - URL shortener service.
- [ ] Rally - Meeting and event scheduling tool.
- [ ] IT tools - Collection of useful IT tools and utilities.
- [ ] Ntfy - Simple notification service for sending push notifications.
- [ ] Mealie - Recipe management and meal planning application.

## Usage

> [!WARNING]
> All the services in this repository are designed to be deployed using [Pangolin](https://github.com/fosrl/pangolin), an identity-based, multi-site remote access platform using WireGuard®. Pangolin simplifies secure access to your self-hosted services without exposing them directly to the internet. It handles authentication and encryption, ensuring that only authorized users can access your services with proper tls certificates.
>
> With that said, I strongly recommend you not to use the `compose.yml` files as-is if you are **NOT** using Pangolin:
>
> - Remove any network reference to `pangolin`.
> - The `ports` directive should be added back to expose the services on your host machine. The `expose` directive only makes the ports accessible to linked services within the same Docker network.
>
> If you encounter any issues or need assistance adapting the configurations for non-Pangolin setups, please feel free to [open an issue](https://github.com/MorganKryze/compose-bookshelf/issues) or reach out for help.

First, clone the repository to your local machine:

```bash
git clone https://github.com/MorganKryze/compose-bookshelf.git
cd compose-bookshelf
```

To deploy a service, simply navigate to the corresponding folder, for example `Jellyfin` would be:

```bash
cd services/media/jellyfin
```

Then, copy the example environment file and customize it as needed:

```bash
cp .env.example .env
nano .env
```

Finally, start the service using Docker Compose:

```bash
docker-compose up -d
```

You may also follow its logs to ensure everything is running smoothly:

```bash
docker-compose logs -f
```

> [!TIP]
> I recommend using [lazydocker](https://github.com/jesseduffield/lazydocker#installation) for easier management and visualization of your Docker containers.

## Contributing

Contributions are welcome! If you have a Docker Compose configuration for a self-hosted service that you'd like to share, please feel free to open a pull request.

When adding a new service, please ensure that your Docker Compose file is well-documented and includes any necessary configuration files or instructions for deployment. If the install process requires more than just updating variables in a `.env` file, please include a separate `README.md` in the service folder with detailed instructions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details. That means you are free to use, modify, and distribute the code as long as you include the original license.
