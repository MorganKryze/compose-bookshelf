# Compose Bookshelf

This repository is collection of Docker Compose configurations for self-hosters who want to deploy their own services quickly and easily. Each folder contains a ready-to-use Docker Compose file along with necessary configuration files.

Feel free to explore the different services and deploy them on your own infrastructure!

> [!NOTE]
> If you do not know where to start with the hardware, have a look at this other project of mine! [MyHomeNAS](https://github.com/MorganKryze/MyHomeNAS)

## Available Services

[Awesome docker compose](https://awesome-docker-compose.com/apps#understanding-the-app-page-structure) and [Awesome self-hosted](https://awesome-selfhosted.net/) lists are great resources to discover new or specific self-hosted applications, I definitely recommend checking them out!

### Security & privacy

- [ ] SearXNG - Privacy-respecting metasearch engine. ([project link](https://github.com/searxng/searxng))
- [ ] Vaultwarden - Self-hosted password manager. ([project link](https://github.com/dani-garcia/vaultwarden))
- [ ] Enclosed - Secure pastebin and tiny file sharing service. ([project link](https://github.com/CorentinTh/enclosed))

### Finances

- [x] [Sure](./services/finances/sure/compose.yml) - Personal finance and budgeting tool. ([project link](https://github.com/we-promise/sure))
- [ ] Wapy.dev - Subsciption tracker and bill reminder service. ([project link](https://github.com/meceware/wapy.dev))

### Online editors

- [x] [Excalidraw](./services/editors/excalidraw/compose.yml) - Virtual whiteboard for sketching and diagramming. ([project link](https://github.com/excalidraw/excalidraw?tab=readme-ov-file))
- [x] [Drawio](./services/editors/drawio/compose.yml) - Diagramming tool for creating flowcharts and diagrams. ([project link](https://github.com/jgraph/drawio))
- [ ] Etherpad - Collaborative real-time text editor. ([project link](https://github.com/ether/etherpad-lite))
- [x] [Docmost](./services/editors/docmost/compose.yml) - Collaborative markdown editor with live preview. ([project link](https://github.com/docmost/docmost))

### Files

- [x] [FileBrowser Quantum](./services/files/filebrowser/compose.yml) - Web-based file manager for browsing and managing files. ([project link](https://github.com/gtsteffaniak/filebrowser))
- [ ] Erugo - Simple file hosting and sharing service. ([project link](https://github.com/ErugoOSS/Erugo))
- [ ] Immich - Image and video backup solution with web interface. ([project link](https://github.com/immich-app/immich))
- [ ] Kiwix - Offline reader for web content like Wikipedia. ([project link](https://github.com/kiwix/kiwix-tools/tree/main))

### Media

- [ ] Jellyfin - Media server for streaming your personal media collection. ([project link](https://github.com/jellyfin/jellyfin))
- [ ] Jellyseerr - Media request and management tool for Jellyfin. ([project link](https://github.com/seerr-team/seerr))
- [ ] JellyStat - Statistics and analytics for your Jellyfin server. ([project link](https://github.com/CyferShepard/Jellystat))
- [x] [Wizarr](./services/media/wizarr/compose.yml) - Invitations and user management for Jellyfin. ([project link](https://github.com/wizarrrr/wizarr))
- [x] [Calibre-Web](./services/media/calibre/compose.yml) - Web-based interface for managing your eBook collection. ([project link](https://github.com/janeczku/calibre-web))

### Media conversion

- [x] [StirlingPDF](./services/media-conversion/stirling-pdf/compose.yml) - PDF conversion and manipulation service. ([project link](https://github.com/Stirling-Tools/Stirling-PDF))
- [x] [ConvertX](./services/media-conversion/convertx/compose.yml) - General file conversion service for images and videos. ([project link](https://github.com/C4illin/ConvertX))
- [ ] Omnitools - A suite of media conversion and processing tools. ([project link](https://github.com/iib0011/omni-tools))
- [ ] Mazanoke - Picture file conversion and management service. ([project link](https://github.com/civilblur/mazanoke))

### Monitoring

- [x] [Uptime Kuma](./services/monitoring/uptime-kuma/compose.yml) - Self-hosted monitoring tool for websites and services. ([project link](https://github.com/louislam/uptime-kuma))

### Miscellaneous

- [ ] OpenSpeedTest - Self-hosted internet speed test service. ([project link](https://github.com/openspeedtest/Speed-Test))
- [ ] LinkStack - Home to all your important links and contacts. ([project link](https://github.com/LinkStackOrg/LinkStack))
- [ ] Kutt - URL shortener service. ([project link](https://github.com/thedevs-network/kutt))
- [ ] Rally - Meeting and event scheduling tool. ([project link](https://github.com/lukevella/rallly))
- [x] [IT tools](./services/misc/it-tools/compose.yml) - Collection of useful IT tools and utilities. ([project link](https://github.com/CorentinTh/it-tools))
- [ ] Ntfy - Simple notification service for sending push notifications. ([project link](https://github.com/binwiederhier/ntfy))
- [ ] Mealie - Recipe management and meal planning application. ([project link](https://github.com/mealie-recipes/mealie))

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
