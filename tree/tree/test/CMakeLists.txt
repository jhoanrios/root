
ROOT_GENERATE_DICTIONARY(ElementStructDict ElementStruct.h LINKDEF ElementStructLinkDef.h OPTIONS -inlineInputHeader)
ROOT_ADD_GTEST(testTOffsetGeneration TOffsetGeneration.cxx ElementStruct.cxx ElementStructDict.cxx
  COPY_TO_BUILDDIR ElementStruct.h
  LIBRARIES RIO Tree MathCore
)
target_include_directories(testTOffsetGeneration PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
ROOT_STANDARD_LIBRARY_PACKAGE(SillyStruct NO_INSTALL_HEADERS HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/SillyStruct.h SOURCES SillyStruct.cxx LINKDEF SillyStructLinkDef.h DEPENDENCIES RIO)
ROOT_ADD_GTEST(testBulkApi BulkApi.cxx LIBRARIES RIO Tree TreePlayer)
ROOT_ADD_GTEST(testBulkApiMultiple BulkApiMultiple.cxx LIBRARIES RIO Tree TreePlayer)
ROOT_ADD_GTEST(testBulkApiVarLength BulkApiVarLength.cxx LIBRARIES RIO Tree TreePlayer)
ROOT_ADD_GTEST(testBulkApiSillyStruct BulkApiSillyStruct.cxx LIBRARIES RIO Tree TreePlayer SillyStruct)
ROOT_ADD_GTEST(testTBasket TBasket.cxx LIBRARIES RIO Tree)
ROOT_ADD_GTEST(testTBranch TBranch.cxx LIBRARIES RIO Tree MathCore)
ROOT_ADD_GTEST(testTIOFeatures TIOFeatures.cxx LIBRARIES RIO Tree)
ROOT_ADD_GTEST(testTTreeCluster TTreeClusterTest.cxx LIBRARIES RIO Tree MathCore)
if(imt)
   ROOT_ADD_GTEST(testTTreeImplicitMT ImplicitMT.cxx LIBRARIES RIO Tree)
endif()
ROOT_ADD_GTEST(testTChainSaveAsCxx TChainSaveAsCxx.cxx LIBRARIES RIO Tree)
ROOT_ADD_GTEST(testTTreeTruncatedDatatypes TTreeTruncatedDatatypes.cxx LIBRARIES RIO Tree)
