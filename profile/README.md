# Porelo

### Jail your agents

**Sandboxing AI agents in YOLO mode using Podman and native Java/GraalVM.**

<img align="left" height="400" width="260" src="images/porelo-400.png" alt="Porelo with AI agent in podman">

In YOLO mode an AI agent stops asking "Can I edit this file?" or "Can I run this command?" and
simply does it: modifies code, deletes files, installs packages, runs scripts — unattended.

[Porelo](https://github.com/porelo-ai/porelo) makes that safe anyway. Each agent runs inside a hardened, rootless container with
default-deny outbound networking, a credential vault that keeps the real keys on the host, a git
checkpoint for every run, and a desktop notification for live allow/deny decisions. Work leaves the
box only through review.

### Control tower for multiple agents

The [frontend](https://github.com/porelo-ai/porelo-frontend) works like a control tower: one place to
watch every agent, wherever it runs — locally or on another machine over ssh — and to decide what
it may do next.

### Agents can talk to each other

Agents can talk to each other without leaking data: the
[message sluice](https://github.com/porelo-ai/porelo-message-sluice) lets only plain prose through —
no encoded payloads, no file contents, no credentials — using fixed, reproducible rules rather than
another language model. Use [message matrix](https://github.com/porelo-ai/porelo-message-matrix)
to run a local Matrix server for real-time agent-to-agent and developer-to-agent communication.

<br clear="left"/>

## Repositories

<table>
<tbody>
<tr><th colspan="3" align="left">Core</th></tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo">porelo</a></td>
<td>The CLI, the daemon, the gate and the guarantees they make.</td>
<td><a href="https://github.com/porelo-ai/porelo/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-message-sluice">porelo-message-sluice</a></td>
<td>Lets agents exchange messages without exchanging data: a deterministic egress filter plus local and spool transports.</td>
<td><a href="https://github.com/porelo-ai/porelo-message-sluice/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-message-sluice/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-message-matrix">porelo-message-matrix</a></td>
<td>The Matrix transport: a project's room, where tasks talk.</td>
<td><a href="https://github.com/porelo-ai/porelo-message-matrix/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-message-matrix/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-adapters">porelo-adapters</a></td>
<td>The build readers behind <code>porelo build status</code>, for GitHub and Forgejo Actions, and the contract suite they pass.</td>
<td><a href="https://github.com/porelo-ai/porelo-adapters/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-adapters/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr><th colspan="3" align="left">Frontend</th></tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-frontend">porelo-frontend</a></td>
<td>The Flutter interface; talks to the daemon over its socket, locally or on another machine via ssh.</td>
<td><a href="https://github.com/porelo-ai/porelo-frontend/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-frontend/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-intellij">porelo-intellij</a></td>
<td>The IntelliJ IDEA plugin: review an agent's waiting work in the IDE without checking it out.</td>
<td><a href="https://github.com/porelo-ai/porelo-intellij/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-intellij/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr><th colspan="3" align="left">Agents</th></tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-claude-code">porelo-claude-code</a></td>
<td>Adapter packaging <a href="https://github.com/anthropics/claude-code">Claude Code</a> (<code>porelo-agent-claude</code>).</td>
<td><a href="https://github.com/porelo-ai/porelo-claude-code/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-claude-code/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-pi">porelo-pi</a></td>
<td>Adapter packaging <a href="https://github.com/earendil-works/pi">Pi</a> (<code>porelo-agent-pi</code>).</td>
<td><a href="https://github.com/porelo-ai/porelo-pi/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-pi/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-codex">porelo-codex</a></td>
<td>Adapter packaging <a href="https://github.com/openai/codex">Codex CLI</a>.</td>
<td><a href="https://github.com/porelo-ai/porelo-codex/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-codex/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-agy">porelo-agy</a></td>
<td>Adapter packaging <a href="https://github.com/google-antigravity/antigravity-cli">Antigravity CLI</a> (<code>agy</code>).</td>
<td><a href="https://github.com/porelo-ai/porelo-agy/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-agy/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-omp">porelo-omp</a></td>
<td>Adapter packaging <a href="https://github.com/can1357/oh-my-pi">Oh My Pi</a> (<code>porelo-agent-omp</code>).</td>
<td><a href="https://github.com/porelo-ai/porelo-omp/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-omp/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr><th colspan="3" align="left">Hosts and builds</th></tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-host">porelo-host</a></td>
<td>Brings a project up on a server and takes it down again, owned or rented by the hour: an Ansible collection.</td>
<td><a href="https://github.com/porelo-ai/porelo-host/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-host/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-buildtools">porelo-buildtools</a></td>
<td>The build and test tooling shared by the repositories, published to Maven Central.</td>
<td><a href="https://github.com/porelo-ai/porelo-buildtools/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-buildtools/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-parent">porelo-parent</a></td>
<td>The parent POM of the Java repositories.</td>
<td><a href="https://github.com/porelo-ai/porelo-parent/actions/workflows/build.yml"><img src="https://github.com/porelo-ai/porelo-parent/actions/workflows/build.yml/badge.svg" alt="Build"></a></td>
</tr>
<tr><th colspan="3" align="left">Project</th></tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-project">porelo-project</a></td>
<td>The project definition and planning: <code>project.yml</code> and the cross-repository requirements. No product code.</td>
<td>&mdash;</td>
</tr>
<tr>
<td><a href="https://github.com/porelo-ai/porelo-ai.github.io">porelo-ai.github.io</a></td>
<td>The documentation of every part as one site: <a href="https://porelo-ai.github.io">porelo-ai.github.io</a>.</td>
<td><a href="https://github.com/porelo-ai/porelo-ai.github.io/actions/workflows/site.yml"><img src="https://github.com/porelo-ai/porelo-ai.github.io/actions/workflows/site.yml/badge.svg" alt="Site"></a></td>
</tr>
</tbody>
</table>
