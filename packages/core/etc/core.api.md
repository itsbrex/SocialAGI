## API Report File for "@opensouls/core"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import Anthropic from '@anthropic-ai/sdk';
import { ChatMessageContent as ChatMessageContent_2 } from './Memory.js';
import { EventEmitter } from 'eventemitter3';
import OpenAI from 'openai';
import { ReadableStream as ReadableStream_2 } from 'web-streams-polyfill';
import { RequestOptions as RequestOptions_2 } from 'openai/core';
import { TemplateTag } from 'common-tags';
import { z } from 'zod';
import { ZodSchema } from 'zod';

// @public (undocumented)
export type AnthropicClientConfig = ConstructorParameters<typeof Anthropic>[0];

// @public (undocumented)
export type AnthropicCompletionParams = Anthropic["messages"]["stream"]["arguments"][0];

// @public (undocumented)
export type AnthropicDefaultCompletionParams = AnthropicCompletionParams & {
    model: AnthropicCompletionParams["model"] | string;
};

// @public (undocumented)
export class AnthropicProcessor implements Processor {
    constructor({ clientOptions, defaultRequestOptions, defaultCompletionParams, customClient }: AnthropicProcessorOpts);
    // (undocumented)
    static label: string;
    // (undocumented)
    process<SchemaType = string>(opts: ProcessOpts<SchemaType>): Promise<ProcessResponse<SchemaType>>;
}

// @public (undocumented)
export interface AnthropicProcessorOpts {
    // (undocumented)
    clientOptions?: AnthropicClientConfig;
    // (undocumented)
    customClient?: ICompatibleAnthropicClient;
    // (undocumented)
    defaultCompletionParams?: Partial<AnthropicDefaultCompletionParams>;
    // (undocumented)
    defaultRequestOptions?: Partial<AnthropicRequestOptions>;
}

// @public (undocumented)
export type AnthropicRequestOptions = Anthropic["messages"]["stream"]["arguments"][1];

// @public (undocumented)
export type ChatMessageContent = string | (ContentText | ContentImage)[];

// @public (undocumented)
export enum ChatMessageRoleEnum {
    // (undocumented)
    Assistant = "assistant",
    // (undocumented)
    Function = "function",
    // (undocumented)
    System = "system",
    // (undocumented)
    User = "user"
}

// @public (undocumented)
export type CognitiveStep<UserArgType, PostProcessReturnType> = {
    (memory: WorkingMemory, userArgs: UserArgType, transformOpts: TransformOptions & {
        stream: true;
    }): Promise<TransformReturnStreaming<PostProcessReturnType>>;
    (memory: WorkingMemory, userArgs: UserArgType, transformOpts?: Omit<TransformOptions, "stream">): Promise<TransformReturnNonStreaming<PostProcessReturnType>>;
    (memory: WorkingMemory, userArgs: UserArgType, transformOpts: Omit<TransformOptions, "stream"> & {
        stream: false;
    }): Promise<TransformReturnNonStreaming<PostProcessReturnType>>;
};

// @public (undocumented)
export type CompatibleAnthropicClient = {
    messages: {
        stream: (body: AnthropicCompletionParams, options?: AnthropicRequestOptions) => AsyncIterable<Anthropic.MessageStreamEvent>;
    };
};

// @public (undocumented)
export type ContentImage = {
    type: "image_url";
    image_url: ImageURL;
};

// @public (undocumented)
export type ContentText = {
    type: "text";
    text: string;
};

// @public
export const createCognitiveStep: <UserArgType = undefined, SchemaType = string, PostProcessType = SchemaType>(transformationOptionsGenerator: (singleArg: UserArgType) => MemoryTransformationOptions<SchemaType, PostProcessType>) => CognitiveStep<UserArgType, PostProcessType>;

// @public (undocumented)
export type CUSTOM_MODEL = `${OrganizationSlug}/${CustomModelName}`;

// @public (undocumented)
export type CustomModelName = string;

// @public (undocumented)
export const debugChatShape: {
    metadata: {};
    state: {};
    eventLog: {
        events: SoulEvent[];
        metadata: EventLogMetadata;
        pendingToolCalls: Record<string, JsonRPCPair>;
    };
};

// @public (undocumented)
export type DeveloperDispatchedPerception = Omit<ExternalPerception, "_id" | "_kind" | "_timestamp">;

// @public (undocumented)
export type DeveloperInteractionRequest = Omit<InteractionRequest, "_id" | "_kind" | "_timestamp" | "content" | "internal"> & {
    content: AsyncIterable<string> | string;
};

// @public (undocumented)
export interface ErroredJsonRPCResponse {
    // (undocumented)
    error: {
        code: number;
        message: string;
        data?: Json;
    };
    // (undocumented)
    id: string;
}

// @public (undocumented)
export type EventLogDoc = typeof eventLogShape;

// @public (undocumented)
export interface EventLogMetadata {
    // (undocumented)
    blueprint?: string;
    // (undocumented)
    environment?: SoulEnvironment;
    // (undocumented)
    id: string;
}

// @public (undocumented)
export const eventLogShape: {
    events: SoulEvent[];
    metadata: EventLogMetadata;
    pendingToolCalls: Record<string, JsonRPCPair>;
};

// @public (undocumented)
export interface ExternalPerception extends PerceptionBase {
    // (undocumented)
    internal?: false;
}

// @public (undocumented)
export function extractJSON(str?: string | null): string | null;

// @public (undocumented)
export function forkStream<T>(originalStream: AsyncIterable<T>, count?: number): ReadableStream_2<T>[];

// @public (undocumented)
export function getProcessor(name: string, opts?: ProcessorCreationOpts): Processor;

// @public (undocumented)
type Headers_2 = Record<string, string | null | undefined>;
export { Headers_2 as Headers }

// @public (undocumented)
export interface ICompatibleAnthropicClient {
    // (undocumented)
    new (options: AnthropicClientConfig): CompatibleAnthropicClient;
}

// @public (undocumented)
export interface ImageURL {
    detail?: 'auto' | 'low' | 'high';
    url: string;
}

// @public (undocumented)
export const indentNicely: TemplateTag;

// @public (undocumented)
export type InputMemory = Omit<Memory, "_id" | "_timestamp"> & {
    _id?: string;
    _timestamp?: number;
};

// @public (undocumented)
export interface InteractionRequest extends SoulEvent {
    // (undocumented)
    _kind: SoulEventKinds.InteractionRequest;
}

// @public (undocumented)
export interface InternalPerception extends PerceptionBase {
    // (undocumented)
    internal: true;
    // @deprecated (undocumented)
    premonition?: string;
}

// @public (undocumented)
export type Json = {
    [key: string]: Json | undefined;
} | Json[] | boolean | null | number | string | undefined;

// @public (undocumented)
export interface JsonRPCCall {
    // (undocumented)
    id: string;
    // (undocumented)
    method: string;
    // (undocumented)
    params: any;
}

// @public (undocumented)
export interface JsonRPCPair {
    // (undocumented)
    request: JsonRPCCall;
    // (undocumented)
    response?: JsonRPCResponse;
}

// @public (undocumented)
export type JsonRPCResponse = SuccessfulJsonRPCResponse | ErroredJsonRPCResponse;

// @public (undocumented)
export interface Memory<MetaDataType = Record<string, unknown>> {
    // (undocumented)
    content: ChatMessageContent;
    // (undocumented)
    _id: string;
    // (undocumented)
    metadata?: MetaDataType;
    // (undocumented)
    name?: string;
    // (undocumented)
    region?: string;
    // (undocumented)
    role: ChatMessageRoleEnum;
    // (undocumented)
    _timestamp: number;
}

// @public (undocumented)
export type MemoryListOrWorkingMemory = InputMemory[] | WorkingMemory;

// @public (undocumented)
export interface MemoryTransformationOptions<SchemaType = string, PostProcessType = SchemaType> {
    // (undocumented)
    command: string | ((workingMemory: WorkingMemory) => InputMemory);
    // (undocumented)
    postProcess?: (originalMemory: WorkingMemory, response: SchemaType) => (Promise<PostProcessReturn<PostProcessType>> | PostProcessReturn<PostProcessType>);
    // (undocumented)
    processor?: string;
    // (undocumented)
    schema?: ZodSchema<SchemaType>;
    // (undocumented)
    skipAutoSchemaAddition?: boolean;
    // (undocumented)
    streamProcessor?: StreamProcessor;
}

// @public (undocumented)
export type OpenAIClientConfig = ConstructorParameters<typeof OpenAI>[0];

// @public (undocumented)
export class OpenAIProcessor implements Processor {
    constructor({ clientOptions, singleSystemMessage, forcedRoleAlternation, defaultRequestOptions, defaultCompletionParams, disableResponseFormat }: OpenAIProcessorOpts);
    // (undocumented)
    static label: string;
    // (undocumented)
    process<SchemaType = string>(opts: ProcessOpts<SchemaType>): Promise<ProcessResponse<SchemaType>>;
}

// @public (undocumented)
export interface OpenAIProcessorOpts {
    // (undocumented)
    clientOptions?: OpenAIClientConfig;
    // (undocumented)
    defaultCompletionParams?: Partial<OpenAI.Chat.Completions.ChatCompletionCreateParams>;
    // (undocumented)
    defaultRequestOptions?: Partial<RequestOptions_2>;
    // (undocumented)
    disableResponseFormat?: boolean;
    // (undocumented)
    forcedRoleAlternation?: boolean;
    // (undocumented)
    singleSystemMessage?: boolean;
}

// @public (undocumented)
export type OrganizationSlug = string;

// @public (undocumented)
export type Perception = ExternalPerception | InternalPerception;

// @public (undocumented)
export interface PerceptionBase extends SoulEvent {
    // (undocumented)
    _kind: SoulEventKinds.Perception;
}

// @public (undocumented)
export type PostProcessReturn<SchemaType> = [InputMemory, SchemaType];

// @public (undocumented)
export const prepareMemoryForJSON: (workingMemory: WorkingMemory, jsonMessage?: string) => WorkingMemory;

// @public (undocumented)
export interface ProcessOpts<SchemaType = string> extends RequestOptions {
    // (undocumented)
    memory: WorkingMemory;
    // (undocumented)
    schema?: ZodSchema<SchemaType>;
}

// @public (undocumented)
export interface Processor {
    // (undocumented)
    process<SchemaType = string>(opts: ProcessOpts<SchemaType>): Promise<ProcessResponse<SchemaType>>;
}

// @public (undocumented)
export interface ProcessorCreationOpts {
}

// @public (undocumented)
export type ProcessorFactory = (opts?: ProcessorCreationOpts) => Processor;

// @public
export interface ProcessorSpecification {
    // (undocumented)
    name: string;
    // (undocumented)
    options?: Record<string, any>;
}

// @public (undocumented)
export interface ProcessResponse<SchemaType = string> {
    // (undocumented)
    parsed: Promise<SchemaType>;
    // (undocumented)
    rawCompletion: Promise<string>;
    // (undocumented)
    stream: AsyncIterable<string>;
    // (undocumented)
    usage: Promise<UsageNumbers>;
}

// @public (undocumented)
export function registerProcessor(name: string, processor: ProcessorFactory): void;

// @public (undocumented)
export interface RequestOptions {
    // (undocumented)
    additionalRequestOptions?: Record<string, any>;
    // (undocumented)
    headers?: Headers_2;
    // (undocumented)
    maxTokens?: number;
    // (undocumented)
    model?: SupportedModel;
    // (undocumented)
    signal?: AbortSignal;
    // (undocumented)
    tags?: Record<string, string>;
    // (undocumented)
    temperature?: number;
    // (undocumented)
    timeout?: number;
}

// @public (undocumented)
export type SoulEnvironment = Record<string, Json> | undefined;

// @public (undocumented)
export interface SoulEvent {
    // (undocumented)
    action: string;
    // (undocumented)
    content: string;
    // (undocumented)
    _id: string;
    // (undocumented)
    internal?: boolean;
    // (undocumented)
    _kind: SoulEventKinds;
    // (undocumented)
    _mentalProcess?: {
        name: string;
        params: Json;
    };
    // (undocumented)
    _metadata?: Record<string, Json>;
    // (undocumented)
    name?: string;
    // (undocumented)
    _pending?: boolean;
    // (undocumented)
    _timestamp: number;
}

// @public (undocumented)
export enum SoulEventKinds {
    // (undocumented)
    InteractionRequest = "interactionRequest",
    // (undocumented)
    Perception = "perception",
    // (undocumented)
    System = "system"
}

// @public (undocumented)
export type StreamProcessor = (workingMemory: WorkingMemory, stream: AsyncIterable<string>) => (AsyncIterable<string> | Promise<AsyncIterable<string>>);

// @public (undocumented)
export const stripEntityAndVerb: (soulName: string, _verb: string, response: string) => string;

// @public (undocumented)
export const stripEntityAndVerbFromStream: ({ soulName }: WorkingMemory, stream: AsyncIterable<string>) => Promise<AsyncIterable<string>>;

// @public (undocumented)
export interface SuccessfulJsonRPCResponse {
    // (undocumented)
    id: string;
    // (undocumented)
    result: Json;
}

// @public (undocumented)
export const SUPPORTED_MODELS: string[];

// @public (undocumented)
export type SupportedModel = typeof SUPPORTED_MODELS[number] | CUSTOM_MODEL;

// @public (undocumented)
export interface SystemEvent extends SoulEvent {
    // (undocumented)
    _kind: SoulEventKinds.System;
}

// @public (undocumented)
export type TransformOptions = RequestOptions & {
    stream?: boolean;
    processor?: ProcessorSpecification;
};

// @public (undocumented)
export type TransformReturn<PostProcessType> = TransformReturnStreaming<PostProcessType> | TransformReturnNonStreaming<PostProcessType>;

// @public (undocumented)
export type TransformReturnNonStreaming<PostProcessType> = [WorkingMemory, PostProcessType];

// @public (undocumented)
export type TransformReturnStreaming<PostProcessType> = [WorkingMemory, AsyncIterable<string>, Promise<PostProcessType>];

// @public (undocumented)
export interface UsageNumbers {
    // (undocumented)
    input: number;
    // (undocumented)
    model: SupportedModel;
    // (undocumented)
    output: number;
}

// @public (undocumented)
export class WorkingMemory extends EventEmitter {
    constructor({ soulName, memories, postCloneTransformation, processor, regionOrder }: WorkingMemoryInitOptions);
    asyncMap(callback: (memory: Memory, i?: number) => Promise<InputMemory>): Promise<WorkingMemory>;
    at(index: number): Memory<Record<string, unknown>>;
    clone(replacementMemories?: InputMemory[], overrides?: Partial<{
        regionOrder: string[];
    }>): WorkingMemory;
    concat(other: MemoryListOrWorkingMemory): WorkingMemory;
    // (undocumented)
    protected doTransform<SchemaType, PostProcessType>(transformation: MemoryTransformationOptions<SchemaType, PostProcessType>, opts: TransformOptions): Promise<(AsyncIterable<string> | this | Promise<unknown>)[] | (this | SchemaType | PostProcessType)[]>;
    filter(callback: (memory: Memory, i?: number) => boolean): WorkingMemory;
    find(callback: (memory: Memory) => boolean): {
        role: ChatMessageRoleEnum;
        content: ChatMessageContent_2;
        name?: string | undefined;
        region?: string | undefined;
        metadata?: Record<string, unknown> | undefined;
        _id: string;
        _timestamp: number;
    } | undefined;
    get finished(): Promise<void>;
    // (undocumented)
    readonly id: string;
    get length(): number;
    map(callback: (memory: Memory, i?: number) => InputMemory): WorkingMemory;
    // (undocumented)
    protected markPending(): void;
    get memories(): Memory<Record<string, unknown>>[];
    orderRegions(...regionOrder: string[]): WorkingMemory;
    prepend(otherWorkingMemory: MemoryListOrWorkingMemory): WorkingMemory;
    // (undocumented)
    processor: ProcessorSpecification;
    // (undocumented)
    protected regionOrder?: string[];
    replace(replacementMemories: InputMemory[]): WorkingMemory;
    // (undocumented)
    protected resolvePending(): void;
    slice(start: number, end?: number): WorkingMemory;
    some(callback: (memory: Memory) => boolean): boolean;
    // (undocumented)
    soulName: string;
    splice(start: number, deleteCount: number, ...items: InputMemory[]): WorkingMemory;
    toString(): string;
    transform<SchemaType, PostProcessType>(transformation: MemoryTransformationOptions<SchemaType, PostProcessType>, opts: {
        stream: true;
    } & TransformOptions): Promise<TransformReturnStreaming<PostProcessType>>;
    // (undocumented)
    transform<SchemaType, PostProcessType>(transformation: MemoryTransformationOptions<SchemaType, PostProcessType>, opts?: Omit<TransformOptions, 'stream'>): Promise<TransformReturnNonStreaming<PostProcessType>>;
    // (undocumented)
    transform<SchemaType, PostProcessType>(transformation: MemoryTransformationOptions<SchemaType, PostProcessType>, opts?: {
        stream: false;
    } & Omit<TransformOptions, 'stream'>): Promise<TransformReturnNonStreaming<PostProcessType>>;
    get usage(): {
        model: string;
        input: number;
        output: number;
    };
    withMemory(memory: InputMemory): WorkingMemory;
    withMonologue(content: string): WorkingMemory;
    withOnlyRegions(...regionNames: string[]): WorkingMemory;
    withoutRegions(...regionNames: string[]): WorkingMemory;
    withRegion(regionName: string, ...memories: InputMemory[]): WorkingMemory;
    withRegionalOrder(...regionOrder: string[]): WorkingMemory;
}

// @public (undocumented)
export interface WorkingMemoryInitOptions {
    // (undocumented)
    memories?: InputMemory[];
    // (undocumented)
    postCloneTransformation?: (workingMemory: WorkingMemory) => WorkingMemory;
    // (undocumented)
    processor?: ProcessorSpecification;
    // (undocumented)
    regionOrder?: string[];
    // (undocumented)
    soulName: string;
}

export { z }

// (No @packageDocumentation comment for this package)

```