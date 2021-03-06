licenses(["notice"])

cc_library(
  visibility = ["//visibility:public"],
  deps = [
    ":proto_lib",
  ],
  name = "cc_proto",
)

java_library(
  visibility = ["//visibility:public"],
  name = "java_proto",
  srcs = glob([
    "upstream/java/src/main/java/com/google/protobuf/*.java"
  ]) + [
    ":generate_java_descriptor_proto",
  ]
)

genrule(
  name = "generate_java_descriptor_proto",
  tools = [
    ":protoc",
  ],
  srcs = [
    "upstream/src/google/protobuf/descriptor.proto",
  ],
  cmd = "$(location :protoc) --java_out=$(GENDIR)/third_party/protobuf/java -Ithird_party/protobuf/upstream/src $<",
  outs = [ "java/com/google/protobuf/DescriptorProtos.java" ],
)

genrule(
  name = "generate_py_descriptor_proto",
  tools = [
    ":protoc",
  ],
  srcs = [
    "upstream/src/google/protobuf/descriptor.proto",
    "upstream/src/google/protobuf/compiler/plugin.proto",
  ],
  cmd = "$(location :protoc) --python_out=$(@D) -Ithird_party/protobuf/upstream/src $(SRCS)",
  outs = [
    "google/protobuf/descriptor_pb2.py",
    "google/protobuf/compiler/plugin_pb2.py",
  ],
)

COMMON_COPTS = [
  "-DHAVE_CONFIG_H",
  "-pthread",
  "-Wall",
  "-Wwrite-strings",
  "-Woverloaded-virtual",
  "-Wno-sign-compare",
  "-Wno-error=unused-function",
  "-Ithird_party/protobuf/build/k8",
  "-Ithird_party/protobuf/build/k8/src",
]

cc_library(
  visibility = ["//visibility:public"],
  name = "proto_lib",
  hdrs = [
    "upstream/src/google/protobuf/arena.h",
    "upstream/src/google/protobuf/arenastring.h",
    "upstream/src/google/protobuf/descriptor.h",
    "upstream/src/google/protobuf/descriptor.pb.h",
    "upstream/src/google/protobuf/descriptor_database.h",
    "upstream/src/google/protobuf/dynamic_message.h",
    "upstream/src/google/protobuf/extension_set.h",
    "upstream/src/google/protobuf/generated_enum_reflection.h",
    "upstream/src/google/protobuf/generated_message_reflection.h",
    "upstream/src/google/protobuf/generated_message_util.h",
    "upstream/src/google/protobuf/io/coded_stream.h",
    "upstream/src/google/protobuf/io/coded_stream_inl.h",
    "upstream/src/google/protobuf/io/gzip_stream.h",
    "upstream/src/google/protobuf/io/package_info.h",
    "upstream/src/google/protobuf/io/printer.h",
    "upstream/src/google/protobuf/io/strtod.h",
    "upstream/src/google/protobuf/io/tokenizer.h",
    "upstream/src/google/protobuf/io/zero_copy_stream.h",
    "upstream/src/google/protobuf/io/zero_copy_stream_impl.h",
    "upstream/src/google/protobuf/io/zero_copy_stream_impl_lite.h",
    "upstream/src/google/protobuf/map.h",
    "upstream/src/google/protobuf/map_entry.h",
    "upstream/src/google/protobuf/map_field.h",
    "upstream/src/google/protobuf/map_field_inl.h",
    "upstream/src/google/protobuf/map_type_handler.h",
    "upstream/src/google/protobuf/message.h",
    "upstream/src/google/protobuf/message_lite.h",
    "upstream/src/google/protobuf/metadata.h",
    "upstream/src/google/protobuf/package_info.h",
    "upstream/src/google/protobuf/proto_cast.h",
    "upstream/src/google/protobuf/reflection.h",
    "upstream/src/google/protobuf/reflection_internal.h",
    "upstream/src/google/protobuf/reflection_ops.h",
    "upstream/src/google/protobuf/repeated_field.h",
    "upstream/src/google/protobuf/repeated_field_reflection.h",
    "upstream/src/google/protobuf/service.h",
    "upstream/src/google/protobuf/stubs/atomic_sequence_num.h",
    "upstream/src/google/protobuf/stubs/atomicops.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_aix.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_arm64_gcc.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_arm_gcc.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_arm_qnx.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_atomicword_compat.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_generic_gcc.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_macosx.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_mips_gcc.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_pnacl.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_solaris.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_tsan.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_x86_gcc.h",
    "upstream/src/google/protobuf/stubs/atomicops_internals_x86_msvc.h",
    "upstream/src/google/protobuf/stubs/casts.h",
    "upstream/src/google/protobuf/stubs/common.h",
    "upstream/src/google/protobuf/stubs/fastmem.h",
    "upstream/src/google/protobuf/stubs/hash.h",
    "upstream/src/google/protobuf/stubs/map_util.h",
    "upstream/src/google/protobuf/stubs/once.h",
    "upstream/src/google/protobuf/stubs/platform_macros.h",
    "upstream/src/google/protobuf/stubs/shared_ptr.h",
    "upstream/src/google/protobuf/stubs/singleton.h",
    "upstream/src/google/protobuf/stubs/stl_util.h",
    "upstream/src/google/protobuf/stubs/stringprintf.h",
    "upstream/src/google/protobuf/stubs/strutil.h",
    "upstream/src/google/protobuf/stubs/substitute.h",
    "upstream/src/google/protobuf/stubs/template_util.h",
    "upstream/src/google/protobuf/stubs/type_traits.h",
    "upstream/src/google/protobuf/text_format.h",
    "upstream/src/google/protobuf/unknown_enum_impl.h",
    "upstream/src/google/protobuf/unknown_field_set.h",
    "upstream/src/google/protobuf/wire_format.h",
    "upstream/src/google/protobuf/wire_format_lite.h",
    "upstream/src/google/protobuf/wire_format_lite_inl.h",
  ],

  includes = [
    "upstream/src",
    # "upstream",
  ],
  copts = COMMON_COPTS,
  srcs = [
    "upstream/src/google/protobuf/arena.cc",
    "upstream/src/google/protobuf/arenastring.cc",
    "upstream/src/google/protobuf/descriptor.cc",
    "upstream/src/google/protobuf/descriptor.pb.cc",
    "upstream/src/google/protobuf/descriptor_database.cc",
    "upstream/src/google/protobuf/dynamic_message.cc",
    "upstream/src/google/protobuf/extension_set.cc",
    "upstream/src/google/protobuf/extension_set_heavy.cc",
    "upstream/src/google/protobuf/generated_message_reflection.cc",
    "upstream/src/google/protobuf/generated_message_util.cc",
    "upstream/src/google/protobuf/io/coded_stream.cc",
    "upstream/src/google/protobuf/io/gzip_stream.cc",
    "upstream/src/google/protobuf/io/printer.cc",
    "upstream/src/google/protobuf/io/strtod.cc",
    "upstream/src/google/protobuf/io/tokenizer.cc",
    "upstream/src/google/protobuf/io/zero_copy_stream.cc",
    "upstream/src/google/protobuf/io/zero_copy_stream_impl.cc",
    "upstream/src/google/protobuf/io/zero_copy_stream_impl_lite.cc",
    "upstream/src/google/protobuf/map_field.cc",
    "upstream/src/google/protobuf/message.cc",
    "upstream/src/google/protobuf/message_lite.cc",
    "upstream/src/google/protobuf/reflection_ops.cc",
    "upstream/src/google/protobuf/repeated_field.cc",
    "upstream/src/google/protobuf/service.cc",
    "upstream/src/google/protobuf/stubs/atomicops_internals_x86_gcc.cc",
    "upstream/src/google/protobuf/stubs/atomicops_internals_x86_msvc.cc",
    "upstream/src/google/protobuf/stubs/common.cc",
    "upstream/src/google/protobuf/stubs/once.cc",
    "upstream/src/google/protobuf/stubs/stringprintf.cc",
    "upstream/src/google/protobuf/stubs/structurally_valid.cc",
    "upstream/src/google/protobuf/stubs/strutil.cc",
    "upstream/src/google/protobuf/stubs/substitute.cc",
    "upstream/src/google/protobuf/text_format.cc",
    "upstream/src/google/protobuf/unknown_field_set.cc",
    "upstream/src/google/protobuf/wire_format.cc",
    "upstream/src/google/protobuf/wire_format_lite.cc",
  ],
  linkopts = [
    "-lz",
  ],
)

cc_library(
  name = "protoc_lib",
  visibility = ["//visibility:public"],
  copts = COMMON_COPTS,
  deps = [
    ":proto_lib",
  ],
  hdrs = [
    "upstream/src/google/protobuf/compiler/code_generator.h",
    "upstream/src/google/protobuf/compiler/command_line_interface.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_enum.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_enum_field.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_extension.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_field.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_file.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_generator.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_helpers.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_map_field.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_message.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_message_field.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_options.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_primitive_field.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_service.h",
    "upstream/src/google/protobuf/compiler/cpp/cpp_string_field.h",
    "upstream/src/google/protobuf/compiler/importer.h",
    "upstream/src/google/protobuf/compiler/java/java_context.h",
    "upstream/src/google/protobuf/compiler/java/java_doc_comment.h",
    "upstream/src/google/protobuf/compiler/java/java_enum.h",
    "upstream/src/google/protobuf/compiler/java/java_enum_field.h",
    "upstream/src/google/protobuf/compiler/java/java_extension.h",
    "upstream/src/google/protobuf/compiler/java/java_field.h",
    "upstream/src/google/protobuf/compiler/java/java_file.h",
    "upstream/src/google/protobuf/compiler/java/java_generator.h",
    "upstream/src/google/protobuf/compiler/java/java_generator_factory.h",
    "upstream/src/google/protobuf/compiler/java/java_helpers.h",
    "upstream/src/google/protobuf/compiler/java/java_lazy_message_field.h",
    "upstream/src/google/protobuf/compiler/java/java_map_field.h",
    "upstream/src/google/protobuf/compiler/java/java_message.h",
    "upstream/src/google/protobuf/compiler/java/java_message_field.h",
    "upstream/src/google/protobuf/compiler/java/java_name_resolver.h",
    "upstream/src/google/protobuf/compiler/java/java_names.h",
    "upstream/src/google/protobuf/compiler/java/java_primitive_field.h",
    "upstream/src/google/protobuf/compiler/java/java_service.h",
    "upstream/src/google/protobuf/compiler/java/java_shared_code_generator.h",
    "upstream/src/google/protobuf/compiler/java/java_string_field.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_enum.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_enum_field.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_extension.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_field.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_file.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_generator.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_helpers.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_map_field.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_message.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_message_field.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_params.h",
    "upstream/src/google/protobuf/compiler/javanano/javanano_primitive_field.h",
    "upstream/src/google/protobuf/compiler/package_info.h",
    "upstream/src/google/protobuf/compiler/parser.h",
    "upstream/src/google/protobuf/compiler/plugin.h",
    "upstream/src/google/protobuf/compiler/plugin.pb.h",
    "upstream/src/google/protobuf/compiler/python/python_generator.h",
    "upstream/src/google/protobuf/compiler/ruby/ruby_generator.h",
    "upstream/src/google/protobuf/compiler/subprocess.h",
    "upstream/src/google/protobuf/compiler/zip_writer.h",
  ],
  srcs = [
    "upstream/src/google/protobuf/compiler/code_generator.cc",
    "upstream/src/google/protobuf/compiler/command_line_interface.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_enum.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_enum_field.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_extension.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_field.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_file.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_generator.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_helpers.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_map_field.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_message.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_message_field.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_primitive_field.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_service.cc",
    "upstream/src/google/protobuf/compiler/cpp/cpp_string_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_repeated_primitive_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_field_base.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_extension.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_source_generator_base.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_generator.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_repeated_message_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_message_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_primitive_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_repeated_enum_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_enum_field.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_enum.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_message.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_helpers.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_writer.cc",
    "upstream/src/google/protobuf/compiler/csharp/csharp_umbrella_class.cc",
    "upstream/src/google/protobuf/compiler/importer.cc",
    "upstream/src/google/protobuf/compiler/java/java_context.cc",
    "upstream/src/google/protobuf/compiler/java/java_doc_comment.cc",
    "upstream/src/google/protobuf/compiler/java/java_enum.cc",
    "upstream/src/google/protobuf/compiler/java/java_enum_field.cc",
    "upstream/src/google/protobuf/compiler/java/java_extension.cc",
    "upstream/src/google/protobuf/compiler/java/java_field.cc",
    "upstream/src/google/protobuf/compiler/java/java_file.cc",
    "upstream/src/google/protobuf/compiler/java/java_generator.cc",
    "upstream/src/google/protobuf/compiler/java/java_generator_factory.cc",
    "upstream/src/google/protobuf/compiler/java/java_helpers.cc",
    "upstream/src/google/protobuf/compiler/java/java_lazy_message_field.cc",
    "upstream/src/google/protobuf/compiler/java/java_map_field.cc",
    "upstream/src/google/protobuf/compiler/java/java_message.cc",
    "upstream/src/google/protobuf/compiler/java/java_message_field.cc",
    "upstream/src/google/protobuf/compiler/java/java_name_resolver.cc",
    "upstream/src/google/protobuf/compiler/java/java_primitive_field.cc",
    "upstream/src/google/protobuf/compiler/java/java_service.cc",
    "upstream/src/google/protobuf/compiler/java/java_shared_code_generator.cc",
    "upstream/src/google/protobuf/compiler/java/java_string_field.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_enum.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_enum_field.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_extension.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_field.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_file.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_generator.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_helpers.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_map_field.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_message.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_message_field.cc",
    "upstream/src/google/protobuf/compiler/javanano/javanano_primitive_field.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_message_field.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_primitive_field.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_enum.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_generator.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_file.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_enum_field.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_extension.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_oneof.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_helpers.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_map_field.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_field.cc",
    "upstream/src/google/protobuf/compiler/objectivec/objectivec_message.cc",
    "upstream/src/google/protobuf/compiler/parser.cc",
    "upstream/src/google/protobuf/compiler/plugin.cc",
    "upstream/src/google/protobuf/compiler/plugin.pb.cc",
    "upstream/src/google/protobuf/compiler/python/python_generator.cc",
    "upstream/src/google/protobuf/compiler/ruby/ruby_generator.cc",
    "upstream/src/google/protobuf/compiler/subprocess.cc",
    "upstream/src/google/protobuf/compiler/zip_writer.cc",
  ],
)

cc_binary(
  name = "protoc",
  visibility = ["//visibility:public"],
  deps = [
    ":protoc_lib",
    ":proto_lib",
  ],
  copts = COMMON_COPTS,
  srcs = [
    "upstream/src/google/protobuf/compiler/main.cc",
  ],
)

py_library(
  visibility = ["//visibility:public"],
  srcs = [
    ":generate_py_descriptor_proto",
    "upstream/python/google/protobuf/internal/api_implementation.py",
    "upstream/python/google/protobuf/internal/containers.py",
    "upstream/python/google/protobuf/internal/cpp_message.py",
    "upstream/python/google/protobuf/internal/decoder.py",
    "upstream/python/google/protobuf/internal/encoder.py",
    "upstream/python/google/protobuf/internal/enum_type_wrapper.py",
    "upstream/python/google/protobuf/internal/message_listener.py",
    "upstream/python/google/protobuf/internal/python_message.py",
    "upstream/python/google/protobuf/internal/type_checkers.py",
    "upstream/python/google/protobuf/internal/wire_format.py",
    "upstream/python/google/protobuf/descriptor.py",
    "upstream/python/google/protobuf/message.py",
    "upstream/python/google/protobuf/descriptor_database.py",
    "upstream/python/google/protobuf/descriptor_pool.py",
    "upstream/python/google/protobuf/message_factory.py",
    "upstream/python/google/protobuf/reflection.py",
    "upstream/python/google/protobuf/service.py",
    "upstream/python/google/protobuf/service_reflection.py",
    "upstream/python/google/protobuf/text_format.py",
  ],
  name = "py_proto",
)

cc_library(
  name = "pyext",
  srcs = [
    "upstream/python/google/protobuf/pyext/descriptor.cc",
    "upstream/python/google/protobuf/pyext/descriptor_containers.cc",
    "upstream/python/google/protobuf/pyext/descriptor_pool.cc",
    "upstream/python/google/protobuf/pyext/message.cc",
    "upstream/python/google/protobuf/pyext/extension_dict.cc",
    "upstream/python/google/protobuf/pyext/repeated_scalar_container.cc",
    "upstream/python/google/protobuf/pyext/repeated_composite_container.cc"
  ],
  copts = [
    "-I",
    "/usr/include/python2.7",
    "-Ithird_party/protobuf/upstream/python",
  ] + COMMON_COPTS,
  deps = [
    ":proto_lib",
  ]
)
