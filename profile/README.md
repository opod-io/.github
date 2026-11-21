# Opod

**Serve open-weight models on the GPUs you already own.** One OpenAI-compatible endpoint across many machines, engine-agnostic, nothing leaves your network.

| Repository | What it is | Licence |
|---|---|---|
| [**opod-core**](https://github.com/opod-io/opod-core) | The inference runtime. `opod up` on a leader, `opod join` on each worker: an OpenAI- and Anthropic-compatible gateway, API keys, load-aware routing, and one model sharded across machines (llama.cpp RPC, vLLM + Ray, SGLang). Drives vLLM, SGLang, TensorRT-LLM, llama.cpp, MLX-LM and Ollama. Its `pkg/` is the Go contract a manager imports — `/admin/v1` wire types, the leader–worker node protocol, the environment contract and the model catalog — standard library only. | Apache-2.0 |
| **Control plane** | Installs into any Kubernetes cluster with one `helm install`: a console, a per-GPU VRAM ledger and placer, scale to zero, verified rollouts, usage export, SSO. Never on the request path. Free up to 4 GPUs in total. | Proprietary, [opod.io](https://opod.io) |

```bash
curl -fsSL https://raw.githubusercontent.com/opod-io/opod-core/main/installer/install.sh | sh
opod up            # one machine is a cluster; point Cursor, Aider or any OpenAI SDK at it
```

Questions and design talk: [Discussions](https://github.com/opod-io/opod-core/discussions). Security: [report privately](https://github.com/opod-io/opod-core/security/policy).
